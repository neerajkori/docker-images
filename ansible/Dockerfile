# Base image for the icinga2core container.
FROM centos:7

#Importing public key for centos repository.
RUN set -xe \
#    rpm --import https://www.centos.org/keys/RPM-GPG-KEY-CentOS-7 \
    && yum -y update --nogpgcheck --setopt=tsflags=nodocs \
    && yum clean all \
    && rm -rvf /var/cache/yum/x86_64/7/* 

# Installing the ansible-master packages.
RUN set -ex  \
    yum -y  install --nogpgcheck --setopt=tsflags=nodocs \
#--setopt=tsflags=nodocs  \
    epel-release \
    ansible \
    vim \
    net-tools \
    openssh-server \
    openssh-clients \
    && yum clean all \
    && rm -rvf /var/cache/yum/x86_64/7/* 

# Setting root password within container.
RUN echo 'root:root123' | chpasswd

# Exposing port to outside the container.
EXPOSE 22

# Container initial command to startup
CMD ["/usr/sbin/sshd", "-D"]
