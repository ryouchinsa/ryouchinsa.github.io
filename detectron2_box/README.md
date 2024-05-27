# [RectLabel](https://rectlabel.com)
How to use? Read our [Help page](https://rectlabel.com/help/).

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

# Train bounding boxes using a Faster R-CNN model on Detectron2
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
- [Create box](https://rectlabel.com/edit/#create-box)

To export your custom dataset, use Export menus.
- [Export COCO JSON file](https://rectlabel.com/export/#export-coco-json-file)
- [Export augmented images](https://rectlabel.com/export/#export-augmented-images)

![augment_box](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/c2115227-f23d-46f7-ae7d-02c37ee09bf6)

This is the training script.
```
import os

from detectron2 import model_zoo
from detectron2.config import get_cfg
from detectron2.data.datasets import register_coco_instances
from detectron2.engine import DefaultTrainer
from detectron2.evaluation import COCOEvaluator

class Trainer(DefaultTrainer):
    @classmethod
    def build_evaluator(cls, cfg, dataset_name, output_folder=None):
        return COCOEvaluator(dataset_name, output_folder)

def main():
    images_path = "person/images"
    annotations_path = "person/coco_polygon.json"
    register_coco_instances("dataset_train", {}, annotations_path, images_path)
    cfg = get_cfg()
    cfg.merge_from_file(model_zoo.get_config_file("COCO-Detection/faster_rcnn_R_50_FPN_3x.yaml"))
    cfg.DATASETS.TRAIN = ("dataset_train",)
    cfg.DATASETS.TEST = ()
    cfg.MODEL.WEIGHTS = model_zoo.get_checkpoint_url("COCO-Detection/faster_rcnn_R_50_FPN_3x.yaml")
    cfg.MODEL.ROI_HEADS.BATCH_SIZE_PER_IMAGE = 128
    cfg.MODEL.ROI_HEADS.NUM_CLASSES = 1
    # cfg.MODEL.DEVICE = "cpu"
    cfg.SOLVER.BASE_LR = 0.001
    cfg.SOLVER.MAX_ITER = 5000 
    cfg.SOLVER.IMS_PER_BATCH = 2
    cfg.DATALOADER.NUM_WORKERS = 2
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
python ../tools/my_train_box.py
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

def main():
    images_path = "person/test"
    MetadataCatalog.get("dataset_train").set(thing_classes=["person"])
    cfg = get_cfg()
    cfg.merge_from_file(model_zoo.get_config_file("COCO-Detection/faster_rcnn_R_50_FPN_3x.yaml"))
    cfg.MODEL.WEIGHTS = os.path.join(cfg.OUTPUT_DIR, "model_final.pth")
    cfg.MODEL.ROI_HEADS.BATCH_SIZE_PER_IMAGE = 128
    cfg.MODEL.ROI_HEADS.NUM_CLASSES = 1
    cfg.MODEL.ROI_HEADS.SCORE_THRESH_TEST = 0.5
    # cfg.MODEL.DEVICE = "cpu"
    cfg.SOLVER.IMS_PER_BATCH = 1
    predictor = DefaultPredictor(cfg)
    os.makedirs(cfg.OUTPUT_DIR, exist_ok=True)
    image_paths = glob.glob(os.path.join(images_path, "*.jpg"))
    for image_path in image_paths:
        image = cv2.imread(image_path)
        outputs = predictor(image)
        v = Visualizer(image[:, :, ::-1], MetadataCatalog.get("dataset_train"), scale=1.2)
        out = v.draw_instance_predictions(outputs["instances"].to("cpu"))
        output_path = os.path.join(cfg.OUTPUT_DIR, os.path.basename(image_path))
        cv2.imwrite(output_path, out.get_image()[:, :, ::-1])

if __name__ == "__main__":
    main()

```

Run the inference script.
```
cd detectron2/demo
python my_predictor_box.py
```

![clarke-sanders-ybPJ47PMT_M-unsplash](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/91225e7d-4af4-463b-82a0-f3c92e62af48)













