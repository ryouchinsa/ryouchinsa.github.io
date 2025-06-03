# [RectLabel](https://rectlabel.com)
How to use? Read our [Help page](https://rectlabel.com/help/).

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

# Install CUDA, cuDNN, PyTorch, and LibTorch for C++ on Ubuntu 24.04 in 30 minutes

Using the Amazon EC2 g4dn.xlarge instance which costs $0.526/hour, all installations will finish in 30 minutes.

Install packages.
```
sudo apt-get update
sudo apt-get install build-essential tar curl zip unzip autopoint libtool bison libx11-dev libxft-dev libxext-dev libxrandr-dev libxi-dev libxcursor-dev libxdamage-dev libxinerama-dev libxtst-dev cmake libgflags-dev libopencv-dev python3-dev
```

Install CUDA and cuDNN.
```
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2404/x86_64/cuda-keyring_1.1-1_all.deb
sudo dpkg -i cuda-keyring_1.1-1_all.deb
sudo apt install cuda-drivers
nvidia-smi

sudo apt install cuda-toolkit-12-8
vi ~/.bashrc
export PATH="/usr/local/cuda/bin${PATH:+:${PATH}}"
export LD_LIBRARY_PATH="/usr/local/cuda/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}"
source ~/.bashrc
nvcc --version

apt-cache search libcudnn
sudo apt install libcudnn9-cuda-12
sudo apt install libcudnn9-dev-cuda-12
```

Install PyTorch.
```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
source ~/.bashrc

conda create --name my_env python=3.10
conda activate my_env
conda install pytorch torchvision torchaudio pytorch-cuda -c pytorch -c nvidia

import torch
torch.cuda.is_available()

pip install opencv-python
import cv2 as cv
print(cv.__version__)
```

Download LibTorch for C++.
```
https://docs.pytorch.org/cppdocs/installing.html
https://pytorch.org/get-started/locally/

# Ubuntu CPU
wget https://download.pytorch.org/libtorch/cpu/libtorch-cxx11-abi-shared-with-deps-2.7.0%2Bcpu.zip
unzip libtorch-cxx11-abi-shared-with-deps-2.7.0+cpu.zip
rm libtorch-cxx11-abi-shared-with-deps-2.7.0+cpu.zip

# Ubuntu GPU
wget https://download.pytorch.org/libtorch/cu128/libtorch-cxx11-abi-shared-with-deps-2.7.0%2Bcu128.zip
unzip libtorch-cxx11-abi-shared-with-deps-2.7.0+cu128.zip
rm libtorch-cxx11-abi-shared-with-deps-2.7.0+cu128.zip
```


















