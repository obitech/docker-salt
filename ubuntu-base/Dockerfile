# SaltStack Docker Ubuntu 16.04 Xenial base image
FROM ubuntu:xenial

LABEL   maintainer="obitech@f0rkd.net" \
        release="xenial" \
        version="16.04" 

# Enable the necessary sources and upgrade to latest 
RUN echo "deb http://archive.ubuntu.com/ubuntu xenial main universe multiverse restricted" > /etc/apt/sources.list && \
    echo "deb http://archive.ubuntu.com/ubuntu xenial-security main universe multiverse restricted" >> /etc/apt/sources.list && \ 
    apt-get update && \ 
    apt-get upgrade -y \
    -o DPkg::options::="--force-confdef" \
    -o DPkg::Options::="--force-confold"

# Adding SaltStack repo
RUN apt-get install python-software-properties software-properties-common wget -y \
    -o DPkg::options::="--force-confdef" \
    -o DPkg::Options::="--force-confold" && \
    wget --quiet -O - https://repo.saltstack.com/apt/ubuntu/16.04/amd64/latest/SALTSTACK-GPG-KEY.pub | apt-key add - && \
    echo "deb http://repo.saltstack.com/apt/ubuntu/16.04/amd64/latest xenial main" > /etc/apt/sources.list.d/saltstack.list && \
    apt-get update

# Install Salt Dependencies
RUN apt-get install -y \ 
    python \ 
    python-yaml \ 
    python-m2crypto \ 
    python-crypto \ 
    msgpack-python \ 
    python-zmq \ 
    python-jinja2 \ 
    python-requests \
    -o DPkg::options::="--force-confdef" \
    -o DPkg::Options::="--force-confold"


