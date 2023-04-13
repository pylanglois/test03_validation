### template MEDICS20 Dockerfile to access S3 and MongoDB ###

FROM ubuntu:20.04
ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y apt-utils fuse git nano wget unzip rclone
    
    ## rclone
    RUN mkdir -p /root/.config/rclone
    ADD rclone.conf /root/.config/rclone 
    ## to use rclone 'mount', fuse from host have to to be expose:
    ## docker run -it --device /dev/fuse --cap-add SYS_ADMIN --security-opt apparmor:unconfined docker_name:tag /bin/bash
    ## otherwise, rclone works in CLI:
    ## docker run -it docker_name:tag /bin/bash

    ## python 3.8
    RUN apt-get install -y python3.8 && \
        ln -s /usr/bin/python3.8 /usr/bin/python
    RUN apt-get install -y python3-distutils python3-apt python3.8-dev zlib1g-dev libpng-dev
    WORKDIR /home
    RUN wget -c https://bootstrap.pypa.io/get-pip.py -O get-pip.py
    RUN python3.8 get-pip.py && rm -f get-pip.py
    #ADD requirements.txt .
    #RUN pip install -r requirements.txt


