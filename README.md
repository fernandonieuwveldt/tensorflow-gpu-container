# Machine Learning Development Container: Python

This repo consist of a Dockerfile + vscode settings for a Machine Learning Development environment. This is a modification of the original tensorflow Dockerfile

On host machine install nvidia toolkit. Taken from the https://github.com/NVIDIA/nvidia-docker repo:
(Assuming you on a Debian based system)
```
# Add the package repositories
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt-get update && sudo apt-get install -y nvidia-container-toolkit
sudo systemctl restart docker
```
If you are running linux mint, (this repo was built using Linux Mint 19.3 Cinnamon) set:
```
distribution=ubuntu18.04
```

To build:
```
docker build . -t mldev:gpu
```

To spin up container with gpu:
```
docker run --gpus all -it --rm mldev:gpu bash
```

To start a jupyter notebook:
```
jupyter notebook --ip 0.0.0.0 --no-browser --allow-root
```
