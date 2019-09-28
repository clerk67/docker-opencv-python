FROM python:3.7-slim

ENV OPENCV_VERSION 4.1.1

RUN apt-get update \
  && apt-get install -y cmake curl g++ \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

RUN pip install --upgrade pip \
  && pip install numpy

RUN curl -fsSL https://github.com/opencv/opencv/archive/$OPENCV_VERSION.tar.gz | tar xz \
  && curl -fsSL https://github.com/opencv/opencv_contrib/archive/$OPENCV_VERSION.tar.gz | tar xz \
  && mkdir opencv-$OPENCV_VERSION/build \
  && cd opencv-$OPENCV_VERSION/build \
  && cmake -DBUILD_SHARED_LIBS=NO -DCMAKE_BUILD_TYPE=RELEASE -DOPENCV_EXTRA_MODULES_PATH=../../opencv_contrib-$OPENCV_VERSION/modules .. \
  && make install \
  && cd ../.. \
  && rm -rf opencv-$OPENCV_VERSION \
  && rm -rf opencv_contrib-$OPENCV_VERSION
