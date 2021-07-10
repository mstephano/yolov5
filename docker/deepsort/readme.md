# mstephano/yolov5

<img alt="Docker Pulls" src="https://img.shields.io/docker/pulls/mstephano/yolov5_deepsort">

This branch contains a folder named `docker/deepsort` which contains a Dockerfile to build an image with Python and DeepSort (object tracking) for Yolov5.

# Repository
- https://github.com/mstephano/yolov5
- Dockerfile: https://github.com/mstephano/yolov5/blob/master/docker/deepsort/Dockerfile

# Docker Hub
- https://hub.docker.com/repository/docker/mstephano/yolov5_deepsort

# Goal

This Dockerfile builds a smaller image (2.8 GB) than the original image from ultralytics/yolov5 (14.9 GB). This makes inference on CPU/GPU faster on the same video.

# Usage

Run the code below,

```bash
# Windows/Linux/Mac-Intel amd64
docker pull mstephano/yolov5_deepsort:v5.0

# Mac-M1/NVIDIA-Jetson AGX arm64
docker pull mstephano/yolov5_deepsort:v5.0-m1
```

Make sure to clone this repo, and be in the yolov5/docker folder
```bash
git clone https://github.com/mstephano/yolov5.git
cd yolov5/docker
```

## Windows
If you are on Windows, currently it is only possible to run inference on **CPU** using a docker container:
```bash
docker run --rm -it -v ${PWD}/videos/:/usr/src/app/videos/ -v ${PWD}/deepsort_output/:/usr/src/app/inference/ mstephano/yolov5_deepsort:v5.0 /bin/bash -c "python track.py --source ./videos/ --yolo_weights ./videos/yolov5s.pt --save-vid"
```
**NOTE** In order to run on GPU using a docker container on Windows, you must follow this guide: https://docs.nvidia.com/cuda/wsl-user-guide/index.html

## Linux
If you are on Linux, you can run this command to run on **CPU**:
```bash
docker run --rm -it -v ${PWD}/videos/:/usr/src/app/videos/ -v ${PWD}/deepsort_output/:/usr/src/app/inference/ mstephano/yolov5_deepsort:v5.0 /bin/bash -c "python track.py --source ./videos/ --yolo_weights ./videos/yolov5s.pt --save-vid"
```

If you are on Linux, you can run this command to run on **GPU** with NVIDIA graphic card (much faster inference):
```bash
docker run --rm -it --gpus all -v ${PWD}/videos/:/usr/src/app/videos/ -v ${PWD}/deepsort_output/:/usr/src/app/inference/ mstephano/yolov5_deepsort:v5.0 /bin/bash -c "python track.py --source ./videos/ --yolo_weights ./videos/yolov5s.pt --save-vid"
```

## Mac
If you are on Mac with **Intel processor**, you can run this command to run on **CPU**:
```bash
docker run --rm -it -v ${PWD}/videos/:/usr/src/app/videos/ -v ${PWD}/deepsort_output/:/usr/src/app/inference/ mstephano/yolov5_deepsort:v5.0 /bin/bash -c "python track.py --source ./videos/ --yolo_weights ./videos/yolov5s.pt --save-vid"
```

If you are on Mac with Docker Desktop for **Apple silicon M1 processor**, you can run this command to run on **CPU**:
```bash
docker run --rm -it -v ${PWD}/videos/:/usr/src/app/videos/ -v ${PWD}/deepsort_output/:/usr/src/app/inference/ mstephano/yolov5_deepsort:v5.0-m1 /bin/bash -c "python track.py --source ./videos/ --yolo_weights ./videos/yolov5s.pt --save-vid"
```

# User Guide
- Every videos in folder `yolov5/docker/videos` will be processed
- You can put your custom model in folder `yolov5/docker/videos` and use it in the command line by replacing `yolov5s.pt` by your custom model file
- Processed videos will be in folder `yolov5/docker/deepsort_output`

# Credits
- DeepSort for Yolov5 : https://github.com/mikel-brostrom/Yolov5_DeepSort_Pytorch
