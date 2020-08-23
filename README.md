# docker
# Docker Development Environments
This repo contains docker container build files to create C/C++ developers environment under CentOS. The container includes a desktop environment which may be accessed via a VNC client.

## Building
To build the container use the following command in the directory containing the 'Dockerfile':

`docker build . -t name:tag`

## Running
To run the container use the following command:

`docker run -it --name devel --rm -p 5901:5901 name:tag`

It's a good idea to overlay a docker volume over the devel users home directory (/home/devel) to save any modifications in that directory. All other changes will be reverted when the container exits.

Once the container is running use the following command to start a VNC server instance:

`vncserver -geometry 1920x1080`

Once the server is running you can connect to it from the host using hostname and VNC port specified below.

`localhost:1`

## Eclipse
Eclipse CDT is installed under /opt/eclipse
