# RectLabel
An offline image annotation tool for object detection and segmentation.

To download RectLabel apps.
- [RectLabel](https://apps.apple.com/app/id1210181730)
- [RectLabel Pro](https://apps.apple.com/app/id1490990105)

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

Thank you.

# Train Detectron2 models on Ubuntu 22.04
[Detectron2](https://github.com/facebookresearch/detectron2) is Facebook AI Research's next generation library that provides state-of-the-art detection and segmentation algorithms

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

Run training.
```
cd detectron2/demo
vi ../tools/my_train_net.py
cfg.INPUT.MASK_FORMAT = "polygon" # "segmentation" is a polygon array.
cfg.INPUT.MASK_FORMAT = "bitmask" # "segmentation" is a RLE mask.
python ../tools/my_train_net.py
```

Run inference.
```
cd detectron2/demo
python my_predictor.py
```

![andy-hay-GBfNe3ZZjhI-unsplash](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/7ec01e8b-2c89-4584-9b84-0990dd88d915)




















