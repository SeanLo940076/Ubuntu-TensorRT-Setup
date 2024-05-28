# Ubuntu-TensorRT-Setup
 A step-by-step guide to installing NVIDIA TensorRT on Ubuntu systems, including setup for supporting libraries and verification of the installation.

## Prerequisites
- Ubuntu 20.04 or similar
- NVIDIA GPU with CUDA support
- CUDA Toolkit installed (corresponding version)

## Installation Steps
1. **Download TensorRT Package:**
   - Visit the [NVIDIA TensorRT page](https://developer.nvidia.com/tensorrt) and download [Here](https://developer.nvidia.com/downloads/compute/machine-learning/tensorrt/secure/8.6.1/local_repos/nv-tensorrt-local-repo-ubuntu2004-8.6.1-cuda-11.8_1.0-1_amd64.deb) the appropriate version for your system.
   

2. **Install TensorRT:**
> **Note:** Before proceeding, ensure that you replace `os` and `tag` variables below with values corresponding to your Ubuntu and TensorRT/CUDA versions.

```bash
os="ubuntu2004"  # Update according to your Ubuntu version
tag="8.6.1-cuda-11.8"  # Update according to the TensorRT version and CUDA version
sudo dpkg -i nv-tensorrt-local-repo-${os}-${tag}_1.0-1_amd64.deb
sudo cp /var/nv-tensorrt-local-repo-${os}-${tag}/*-keyring.gpg /usr/share/keyrings/
```

```bash
sudo dpkg -i nv-tensorrt-local-repo-ubuntu2004-8.6.1-cuda-11.8_1.0-1_amd64.deb 
sudo cp /var/nv-tensorrt-local-repo-ubuntu2004-8.6.1-cuda-11.8/*-keyring.gpg /usr/share/keyrings/

sudo apt-get update
sudo apt-get -y install tensorrt
```
3. **Install Additional Python Libraries:**
```bash
sudo apt-get update
sudo apt-get -y install tensorrt
python3 -m pip install numpy
sudo apt-get -y install python3-libnvinfer-dev
python3 -m pip install protobuf
sudo apt-get -y install uff-converter-tf
python3 -m pip install numpy onnx
sudo apt-get install onnx-graphsurgeon
```

4. **Verify the installation:**
```bash
dpkg-query -W tensorrt
```

You should see something similar to the following:
```bash
tensorrt	8.6.1.6-1+cuda11.8

```
