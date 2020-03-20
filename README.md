# Machine Learning Development Container: Python

This repo consist of a Dockerfile + vscode settings for a Machine Learning Development environment. This is a modification of the original tensorflow Dockerfile

**ToDo
bash script for host machine installations

To build:
```
docker build .devcontainer/. -t mldev:gpu
```

To spin up container with gpu:
```
docker run --gpus all -it --rm mldev:gpu bash
```

To start a jupyter notebook:
```
jupyter notebook --ip 0.0.0.0 --no-browser --allow-root
```
