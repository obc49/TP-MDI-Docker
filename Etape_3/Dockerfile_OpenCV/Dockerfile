FROM ubuntu:16.04

####################################
MAINTAINER Oumar Roland

####################################
RUN apt-get update
RUN apt-get upgrade -y 
RUN apt-get install -y git 

RUN apt-get install -y apt-utils && \
    apt-get install net-tools && \
    apt-get install -y curl && \
    apt-get install -y --no-install-recommends python python-dev python-pip build-essential cmake git pkg-config libjpeg8-dev libtiff5-dev libjasper-dev libpng12-dev libgtk2.0-dev libavcodec-dev libavformat-dev libswscale-dev libv4l-dev libatlas-base-dev gfortran libavresample-dev libgphoto2-dev libgstreamer-plugins-base1.0-dev libdc1394-22-dev  && \
    apt-get install -y ant && \
    apt-get install -y default-jre && \
    apt-get install -y default-jdk && \
    apt-get install -y openjdk-8-jdk && \
    apt-get install -y maven && \
    apt-get install -y g++ 

####################################    
RUN git clone https://github.com/Itseez/opencv.git
RUN cd opencv \
    && git checkout -b 3.4 origin/3.4 \
    && mkdir build \
    && cd build \
    && cmake -D BUILD_SHARED_LIBS=OFF .. \
    &&  make -j8 


#####################################
CMD ["/bin/bash"]