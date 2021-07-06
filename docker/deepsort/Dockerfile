FROM python:3.8.5-slim-buster as builder

RUN apt-get update && apt-get install ffmpeg libsm6 libxext6 git -y
RUN git clone --recurse-submodules https://github.com/mikel-brostrom/Yolov5_DeepSort_Pytorch.git /usr/src/app
WORKDIR /usr/src/app

RUN pip install --upgrade pip
RUN pip install --default-timeout=100 future requests
RUN pip install --no-cache-dir -r requirements.txt
