FROM centos:7

RUN echo password | passwd --stdin root

RUN yum -y install dialog man man-pages man-db epel-release
RUN yum -y groupinstall "Development tools" "Compatibility libraries"

RUN adduser -u 1000 -U -m devel
RUN echo password | passwd --stdin devel

USER root
WORKDIR /root
RUN echo "mate-session" > ~/.Xclients && chmod a+x ~/.Xclients

# Desktop Installation
RUN yum -y groupinstall "MATE Desktop"
RUN yum -y install tigervnc-server java wget
RUN yum -y update

RUN wget -nv "https://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/2020-06/R/eclipse-cpp-2020-06-R-linux-gtk-x86_64.tar.gz&r=1" -O /opt/eclipse-cpp-2020-06-R-linux-gtk-x86_64.tar.gz

RUN tar xvfz /opt/eclipse-cpp-2020-06-R-linux-gtk-x86_64.tar.gz -C /opt && rm /opt/eclipse-cpp-2020-06-R-linux-gtk-x86_64.tar.gz

USER devel
WORKDIR /home/devel
RUN echo "mate-session" > ~/.Xclients && chmod a+x ~/.Xclients


EXPOSE 5901
