FROM centos:6

# Set the password for root
RUN echo password | passwd --stdin root

# Create the devel user and set the password
RUN adduser -u 1000 -U -m devel
RUN echo password | passwd --stdin devel

# Install the development tools
RUN yum -y install dialog man man-pages man-db epel-release java wget
RUN yum -y groupinstall "Development tools"

# Desktop Installation
RUN yum -y groupinstall Desktop Fonts
RUN yum -y install tigervnc-server

# Update all packages
RUN yum -y update

# Get and install eclipse CDT
RUN wget -nv "https://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/mars/2/eclipse-cpp-mars-2-linux-gtk-x86_64.tar.gz" -O /opt/eclipse-cpp-mars-2-linux-gtk-x86_64.tar.gz
RUN tar xvfz /opt/eclipse-cpp-mars-2-linux-gtk-x86_64.tar.gz -C /opt && rm /opt/eclipse-cpp-mars-2-linux-gtk-x86_64.tar.gz

# Set the default Desktop environment for devel
USER devel
WORKDIR /home/devel

RUN echo "export PATH=/opt/eclipse:$PATH" >> .bashrc

# Advertize the port number used for VNC
EXPOSE 5901
