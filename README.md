# Tensorflow with GPU Docker Container: Python

This repo consist of a Dockerfile for a Tensorflow(GPU) container. This is a modification of the original tensorflow Dockerfile, but striving to be easier to install.
(There is also a branch to use docker-compose, but there is currently not a gpu flag for compose.)

On host machine install nvidia toolkit. Taken from the https://github.com/NVIDIA/nvidia-docker repo:
(Assuming you on a Debian based system)
```bash
# Add the package repositories
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt-get update && sudo apt-get install -y nvidia-container-toolkit
sudo systemctl restart docker
```
If you are running linux mint, (this repo was built using Linux Mint 19.3 Cinnamon) set:
```bash
distribution=ubuntu18.04
```

To build:
```bash
docker build . -t tensorflow
```

To spin up container with gpu:
```bash
docker run --gpus all -it -p 8888:8888 --rm tensorflow bash
```

To start a jupyter notebook, run the following in the docker container:
```bash
jupyter notebook --ip 0.0.0.0 --no-browser --allow-root
```

Can also add an alias to your ~/.bashrc file:
```bash
alias start_tensorflow_container='docker run --gpus all -it \
				                  -v "$(pwd)":/ml-project \
				                  -p 8888:8888 \
				                  tensorflow bash'
```
To spin up container using the alias:
```bash
start_tensorflow_container
```
