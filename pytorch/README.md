# Train Detectron2 models on Ubuntu 22.04
[Detectron2](https://github.com/facebookresearch/detectron2) is Facebook AI Research's next generation library that provides state-of-the-art detection and segmentation algorithms.

Install CUDA and cuDNN.
```
[wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-keyring_1.1-1_all.deb
sudo dpkg -i cuda-keyring_1.1-1_all.deb
sudo apt update
sudo apt install cuda-drivers
reboot
nvidia-smi

sudo apt install cuda-toolkit-11-8
vi ~/.bashrc
export PATH="/usr/local/cuda/bin${PATH:+:${PATH}}"
export LD_LIBRARY_PATH="/usr/local/cuda/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}"
source ~/.bashrc
which nvcc
nvcc --version

apt list libcudnn8 -a
cudnn_version=8.9.7.29
cuda_version=cuda11.8
sudo apt install libcudnn8=${cudnn_version}-1+${cuda_version}
sudo apt install libcudnn8-dev=${cudnn_version}-1+${cuda_version}
sudo apt install libcudnn8-samples=${cudnn_version}-1+${cuda_version}
```

Install PyTorch and OpenCV.
```
sudo apt-get update
sudo apt-get install build-essential tar curl zip unzip autopoint libtool bison libx11-dev libxft-dev libxext-dev libxrandr-dev libxi-dev libxcursor-dev libxdamage-dev libxinerama-dev libxtst-dev

wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
source ~/.bashrc

conda create --name my_env python=3.9
conda activate my_env
conda install pytorch torchvision torchaudio pytorch-cuda=11.8 -c pytorch -c nvidia

import torch
torch.cuda.is_available()

pip install opencv-python
import cv2 as cv
print(cv.__version__)
```

Install Detectron2.
```
git clone https://github.com/facebookresearch/detectron2.git
python -m pip install -e detectron2
```

Download datasets and training/inference scripts.
```
wget https://huggingface.co/datasets/rectlabel/datasets/resolve/main/_detectron2.zip
unzip _detectron2.zip
mv _detectron2/my_train_net.py detectron2/tools
mv _detectron2/my_predictor.py detectron2/demo
mv _detectron2/visualizer.py detectron2/detectron2/utils
mv _detectron2/_test_min_rle_donut detectron2/demo
mv _detectron2/_test_min_bbox detectron2/demo
```

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
    images_path = "_test_min_rle_donut/images"
    annotations_path = "_test_min_rle_donut/coco_train_labels.json"
    register_coco_instances("dataset_train", {}, annotations_path, images_path)
    cfg = get_cfg()
    cfg.merge_from_file(model_zoo.get_config_file("COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x.yaml"))
    cfg.DATASETS.TRAIN = ("dataset_train",)
    cfg.DATASETS.TEST = ()
    cfg.DATALOADER.NUM_WORKERS = 2
    cfg.MODEL.WEIGHTS = model_zoo.get_checkpoint_url("COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x.yaml")  # model zoo の学習済みモデルの重みで初期化
    cfg.SOLVER.IMS_PER_BATCH = 2
    cfg.SOLVER.BASE_LR = 0.001
    cfg.SOLVER.MAX_ITER = 1000 
    cfg.MODEL.ROI_HEADS.BATCH_SIZE_PER_IMAGE = 128
    cfg.MODEL.ROI_HEADS.NUM_CLASSES = 1
    cfg.INPUT.MASK_FORMAT = "polygon" # "segmentation" is a polygon array.
    # cfg.INPUT.MASK_FORMAT = "bitmask" # "segmentation" is a RLE mask.
    # cfg.MODEL.DEVICE = "cpu"
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
python ../tools/my_train_net.py
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
    images_path = "_test_min_rle_donut/images"
    MetadataCatalog.get("thing_classes").set(thing_classes=["donut"])
    cfg = get_cfg()
    cfg.merge_from_file(model_zoo.get_config_file("COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x.yaml"))
    cfg.SOLVER.IMS_PER_BATCH = 1
    cfg.MODEL.ROI_HEADS.BATCH_SIZE_PER_IMAGE = 128
    cfg.MODEL.ROI_HEADS.NUM_CLASSES = 1
    cfg.MODEL.ROI_HEADS.SCORE_THRESH_TEST = 0.5
    # cfg.MODEL.DEVICE = "cpu"
    cfg.MODEL.WEIGHTS = os.path.join(cfg.OUTPUT_DIR, "model_final.pth")
    predictor = DefaultPredictor(cfg)
    os.makedirs(cfg.OUTPUT_DIR, exist_ok=True)
    image_paths = glob.glob(os.path.join(images_path, "*.jpg"))
    for image_path in image_paths:
        image = cv2.imread(image_path)
        outputs = predictor(image)
        v = Visualizer(image[:, :, ::-1], MetadataCatalog.get("thing_classes"), scale=1.2)
        out = v.draw_instance_predictions(outputs["instances"].to("cpu"))
        output_path = os.path.join(cfg.OUTPUT_DIR, os.path.basename(image_path))
        cv2.imwrite(output_path, out.get_image()[:, :, ::-1])

if __name__ == "__main__":
    main()
```

Run the inference script.
```
cd detectron2/demo
python my_predictor.py
```

![andy-hay-GBfNe3ZZjhI-unsplash](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/7ec01e8b-2c89-4584-9b84-0990dd88d915)



















