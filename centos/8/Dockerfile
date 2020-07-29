FROM centos:centos8

RUN (cd /lib/systemd/system/sysinit.target.wants/; \
        for i in *; do \
            [ $i == systemd-tmpfiles-setup.service ] || rm -f $i; \
        done); \
    rm -f /lib/systemd/system/multi-user.target.wants/*; \
    rm -f /etc/systemd/system/*.wants/*; \
    rm -f /lib/systemd/system/local-fs.target.wants/*; \
    rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
    rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
    rm -f /lib/systemd/system/basic.target.wants/*; \
    rm -f /lib/systemd/system/anaconda.target.wants/*;

RUN yum update -y \
    && yum install -y epel-release \
    && yum install -y \
        ca-certificates \
        openssl \
        openssl-devel \
        python3 \
        python3-pip \
        libffi-devel \
        which \
    && yum clean -y all

RUN ln -s /usr/bin/python3.6 /usr/bin/python