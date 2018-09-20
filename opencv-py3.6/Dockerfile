FROM aquintero446/ubuntu16.04:py3.6
MAINTAINER Andres Quintero <aquintero446@gmail.com>

RUN apt-get -y update

RUN apt-get install -y --fix-missing \
    libsm6 \
    libxext6 \
    libxrender-dev \
    libgtk2.0-dev \
    libavcodec-dev \
    libavformat-dev \
    libswscale-dev \
    tesseract-ocr-spa \
    locales
RUN apt-get clean && rm -rf /tmp/* /var/tmp/*
RUN pip --no-cache-dir install \
  opencv-python \
  scikit-image \
  pytesseract \
  pillow \
  easydict \
  pyyaml \
  imutils
RUN locale-gen es_CO.UTF-8
ENV LANG es_CO.UTF-8
ENV LANGUAGE es_CO:es
ENV LC_ALL es_CO.UTF-8
ENV PYTHONIOENCODING UTF-8
WORKDIR /home
