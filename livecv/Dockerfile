# 
# Live CV Dockerfile
#

# Pull base image
FROM ubuntu

# Update repos
RUN apt-get update -y

ENV DEBIAN_FRONTEND noninteractive
ENV DISPLAY :0

RUN dpkg-divert --local --rename --add /sbin/initctl && ln -sf /bin/true /sbin/initctl

# Install desktop environment
RUN apt-get install -y lxde

# Install opencv requirements
RUN apt-get install -y build-essential
RUN apt-get install -y cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
RUN apt-get install -y python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev

# Install global requirements
RUN apt-get install -y libgl1-mesa-dev x11vnc xvfb wget 

# Build opencv
RUN git clone https://github.com/Itseez/opencv.git
RUN cd opencv && git checkout 2.4
RUN mkdir opencv/release
RUN cd opencv/release && cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local .. && make && make install

# Get Qt
RUN apt-get install -y software-properties-common
RUN add-apt-repository ppa:beineri/opt-qt551-trusty 
RUN apt-get update -qq
RUN apt-get install -qq qt55base qt55declarative qt55quick1 qt55quickcontrols qt55script qt55imageformats qt55multimedia

# Set qt path
RUN bash -c 'echo "source /opt/qt55/bin/qt55-env.sh" >> /etc/bash.bashrc'

# Setup display buffer and vnc session
RUN bash -c 'echo "Xvfb $DISPLAY -screen 0 1024x768x16 &" >> /etc/bash.bashrc' 
RUN bash -c 'echo "x11vnc -forever -display $DISPLAY &" >> /etc/bash.bashrc'

# Start desktop
RUN bash -c 'echo "startlxde &" >> /etc/bash.bashrc'

