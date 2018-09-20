FROM aquintero446/opencv:pip3.4.3v2.09.19.2018
MAINTAINER Andres Quintero <aquintero446@gmail.com>

#Configure compiling environment
RUN apt-get install -y git
RUN pip install cython

#Upgrade g++5
RUN add-apt-repository ppa:ubuntu-toolchain-r/test &&\
    apt-get update -y &&\
    apt-get upgrade -y &&\
    update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-5 60 --slave /usr/bin/g++ g++ /usr/bin/g++-5

#Install dependency package
RUN apt-get install -y autoconf automake libtool &&\
    apt-get install -y autoconf-archive &&\
    apt-get install -y pkg-config &&\
    apt-get install -y libpng12-dev &&\
    apt-get install -y libjpeg8-dev &&\
    apt-get install -y libtiff5-dev &&\
    apt-get install -y zlib1g-dev &&\
    apt-get install -y libicu-dev &&\
    apt-get install -y libpango1.0-dev &&\
    apt-get install -y libcairo2-dev

#Install Leptonica 1.74
RUN add-apt-repository ppa:alex-p/tesseract-ocr &&\
    apt-get update &&\
    apt-get install -y libleptonica-dev &&\
    ldconfig

#github repository
RUN git clone https://github.com/tesseract-ocr/tesseract.git /tesseract
WORKDIR /tesseract

#Install Tesseract 4.0
RUN sh autogen.sh  &&\
    ./configure  &&\
    LDFLAGS="-L/usr/local/lib" CFLAGS="-I/usr/local/include" make  &&\
    make install  &&\
    make install -langs  &&\
    ldconfig

RUN export TESSDATA_PREFIX=/usr/share/tesseract-ocr/4.00/tessdata/
RUN apt install -y tesseract-ocr-spa
RUN tesseract -v
RUN pip install pytesseract &&\
    pip install --upgrade imutils
WORKDIR /home

RUN mkdir -p /usr/local/share/tessdata &&\
    mv -v /usr/share/tesseract-ocr/4.00/tessdata/spa.traineddata /usr/local/share/tessdata/
