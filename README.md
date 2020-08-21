# docker
<H1>Docker Development Environments</H1>
This repo contains docker container build files (Dockerfile) to create C/C++ developers environment under CentOS. The container includes a desktop environment which may be accessed via VNC.

<H2>Building</H2>
To build the container use the following command in the directory containing the 'Dockerfile':
<code>docker build . -t name:tag</code>

<H2>Running</H2>
To run the container use the following command:
<code>docker run -it --name devel --rm -p 5901:5901 name:tag</code>
It's a good idea to overlay a docker volume over the devel users home directory (/home/devel) so save any modifications in that directory. All other changes will be reverted when the container exits.

Once the container is running use the following command to start a VNC server instance:
<code>vncserver -geometry 1920x1080</code>
Once the server is running you can connect to it from the host using hostname and VNC port specified below.
<code>localhost:1</code>

<H2>Eclipse</H2>
Eclipse CDT is installed under /opt/eclipse
