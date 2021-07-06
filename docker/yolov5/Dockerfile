FROM python:3.8.5-slim-buster as builder

RUN apt-get update && apt-get install ffmpeg libsm6 libxext6 git -y
RUN git clone https://github.com/ultralytics/yolov5.git /usr/src/app
WORKDIR /usr/src/app

RUN pip install --upgrade pip
RUN pip install --default-timeout=100 future
RUN pip install --no-cache-dir -r requirements.txt
