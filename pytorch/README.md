# [RectLabel](https://rectlabel.com)
How to use? Read our [Help page](https://rectlabel.com/help/).

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

# Install CUDA, cuDNN, PyTorch, LibTorch, and ONNX Runtime on Ubuntu 24.04 in 30 minutes

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
sudo apt-get update
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

pip install opencv-python onnx optimum[onnxruntime-gpu] matplotlib numba
```

Download LibTorch.
```
https://pytorch.org/get-started/locally/

wget https://download.pytorch.org/libtorch/cu128/libtorch-cxx11-abi-shared-with-deps-2.7.0%2Bcu128.zip
unzip libtorch-cxx11-abi-shared-with-deps-2.7.0+cu128.zip
```

Download ONNX Runtime.
```
https://github.com/microsoft/onnxruntime/releases/

wget https://github.com/microsoft/onnxruntime/releases/download/v1.20.0/onnxruntime-linux-x64-gpu-1.20.0.tgz
tar -xzvpf onnxruntime-linux-x64-gpu-1.20.0.tgz
```
















