# [RectLabel](https://rectlabel.com)
An offline image annotation tool for object detection and segmentation.

To download RectLabel apps.
- [RectLabel](https://apps.apple.com/app/id1210181730)
- [RectLabel Pro](https://apps.apple.com/app/id1490990105)

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

# Train RLE masks using a Mask R-CNN model on Detectron2
[Detectron2](https://github.com/facebookresearch/detectron2) is Facebook AI Research's next generation library that provides state-of-the-art detection and segmentation algorithms.

[Install CUDA, cuDNN, and PyTorch](https://rectlabel.com/pytorch/).

Install Detectron2.
```
git clone https://github.com/facebookresearch/detectron2.git
python -m pip install -e detectron2
```

Download training/inference scripts.
```
wget https://huggingface.co/rectlabel/detectron2/resolve/main/detectron2_scripts.zip
unzip detectron2_scripts.zip
mv detectron2_scripts/my_train_*.py detectron2/tools
mv detectron2_scripts/my_predictor_*.py detectron2/demo
mv detectron2_scripts/visualizer.py detectron2/detectron2/utils
```

Download person dataset.
```
wget https://huggingface.co/datasets/rectlabel/datasets/resolve/main/person.zip
unzip person.zip
mv person detectron2/demo
```

To label your custom dataset, use Edit menus.
- [Create polygon using SAM](https://rectlabel.com/edit/#create-polygon-using-sam)
- [Create pixels](https://rectlabel.com/edit/#create-pixels)

To export your custom dataset, use Export menus.
- [Export COCO JSON file](https://rectlabel.com/export/#export-coco-json-file)
- [Export augmented images](https://rectlabel.com/export/#export-augmented-images)

![augment_rle](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/53fb96c2-1962-413b-a0bc-83def9f8b775)

This is the training script.
```
import os
from enum import Enum

from detectron2 import model_zoo
from detectron2.config import get_cfg
from detectron2.data.datasets import register_coco_instances
from detectron2.engine import DefaultTrainer
from detectron2.evaluation import COCOEvaluator

class Trainer(DefaultTrainer):
    @classmethod
    def build_evaluator(cls, cfg, dataset_name, output_folder=None):
        return COCOEvaluator(dataset_name, output_folder)

class MaskType(Enum):
    BOX = 1
    POLYGON = 2
    RLE = 3

def main():
    mask_type = MaskType.RLE
    images_path = "person/images"
    if mask_type == MaskType.POLYGON:
        annotations_path = "person/coco_polygon.json"
    elif mask_type == MaskType.RLE:
        annotations_path = "person/coco_rle.json"
    register_coco_instances("dataset_train", {}, annotations_path, images_path)
    cfg = get_cfg()
    cfg.merge_from_file(model_zoo.get_config_file("COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x.yaml"))
    cfg.DATASETS.TRAIN = ("dataset_train",)
    cfg.DATASETS.TEST = ()
    cfg.MODEL.WEIGHTS = model_zoo.get_checkpoint_url("COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x.yaml")
    cfg.MODEL.ROI_HEADS.BATCH_SIZE_PER_IMAGE = 128
    cfg.MODEL.ROI_HEADS.NUM_CLASSES = 1
    # cfg.MODEL.DEVICE = "cpu"
    cfg.SOLVER.BASE_LR = 0.001
    cfg.SOLVER.MAX_ITER = 10000
    cfg.SOLVER.IMS_PER_BATCH = 2
    cfg.DATALOADER.NUM_WORKERS = 2
    if mask_type == MaskType.POLYGON:
        cfg.INPUT.MASK_FORMAT = "polygon"
    elif mask_type == MaskType.RLE:
        cfg.INPUT.MASK_FORMAT = "bitmask"
    os.makedirs(cfg.OUTPUT_DIR, exist_ok=True)
    trainer = Trainer(cfg)
    trainer.resume_or_load(resume=True)
    trainer.train()

if __name__ == "__main__":
    main()
```

Run the training script.
```
cd detectron2/demo
python ../tools/my_train_rle.py
```

This is the inference script.
```
import cv2
import glob
import os

from detectron2 import model_zoo
from detectron2.config import get_cfg
from detectron2.data.datasets import register_coco_instances
from detectron2.data import MetadataCatalog
from detectron2.engine import DefaultPredictor
from detectron2.utils.visualizer import Visualizer
from detectron2.evaluation import COCOEvaluator, inference_on_dataset
from detectron2.data import build_detection_test_loader
from my_predictor_box import SaveType

def main():
    images_path = "person/test"
    MetadataCatalog.get("dataset_test").set(thing_classes=["person"])
    cfg = get_cfg()
    cfg.merge_from_file(model_zoo.get_config_file("COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x.yaml"))
    cfg.MODEL.WEIGHTS = os.path.join(cfg.OUTPUT_DIR, "model_final.pth")
    cfg.MODEL.ROI_HEADS.BATCH_SIZE_PER_IMAGE = 128
    cfg.MODEL.ROI_HEADS.NUM_CLASSES = 1
    cfg.MODEL.ROI_HEADS.SCORE_THRESH_TEST = 0.5
    # cfg.MODEL.DEVICE = "cpu"
    cfg.SOLVER.IMS_PER_BATCH = 1
    predictor = DefaultPredictor(cfg)
    os.makedirs(cfg.OUTPUT_DIR, exist_ok=True)
    save_type = SaveType.COCO_JSON
    if save_type == SaveType.IMAGE:
        image_paths = glob.glob(os.path.join(images_path, "*.jpg"))
        for image_path in image_paths:
            image = cv2.imread(image_path)
            outputs = predictor(image)
            v = Visualizer(image[:, :, ::-1], MetadataCatalog.get("dataset_test"), scale=1.2)
            out = v.draw_instance_predictions(outputs["instances"].to("cpu"))
            output_path = os.path.join(cfg.OUTPUT_DIR, os.path.basename(image_path))
            cv2.imwrite(output_path, out.get_image()[:, :, ::-1])
    elif save_type == SaveType.COCO_JSON:
        annotations_path = "person/coco_test.json"
        register_coco_instances("dataset_test", {}, annotations_path, images_path)
        evaluator = COCOEvaluator("dataset_test", cfg, False, output_dir=cfg.OUTPUT_DIR)
        val_loader = build_detection_test_loader(cfg, "dataset_test")
        inference_on_dataset(predictor.model, val_loader, evaluator)

if __name__ == "__main__":
    main()
```

Run the inference script.
```
cd detectron2/demo
python my_predictor_segmentation.py
```

![tyler-nix-Jg7UTkxTruQ-unsplash](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/cb878256-5d5c-4841-a919-aed7ac73089f)

If you set `save_type = SaveType.COCO_JSON`, you can save the inference result as coco_instances_results.json in the output folder.
To import the inference result to RectLabel, use Export menus -> Import COCO JSON file.

![inference_rle](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/b44c7abe-7b66-4751-9198-30b85ccbba3d)













