FROM ubuntu:16.04

LABEL maintainer="Bernd Doser <bernd.doser@braintwister.eu>"

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    git \
    git-svn \
    make \
    ninja-build \
    python3 \
    python3-dev \
    python3-pip \
    python3-setuptools \
    software-properties-common \
    vim \
    wget \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

RUN pip3 install --upgrade pip \
 && hash -r pip3 \
 && pip3 install -I pyyaml~=3.12 

# Install gosu
RUN gpg --keyserver ha.pool.sks-keyservers.net --recv-keys B42F6819007F00F88E364FD4036A9C25BF357DD4
RUN curl -o /usr/local/bin/gosu -SL "https://github.com/tianon/gosu/releases/download/1.4/gosu-$(dpkg --print-architecture)" \
    && curl -o /usr/local/bin/gosu.asc -SL "https://github.com/tianon/gosu/releases/download/1.4/gosu-$(dpkg --print-architecture).asc" \
    && gpg --verify /usr/local/bin/gosu.asc \
    && rm /usr/local/bin/gosu.asc \
    && chmod +x /usr/local/bin/gosu

# Set aliases
COPY aliases /tmp/
RUN cat /tmp/aliases >> /etc/bash.bashrc && rm -f /tmp/aliases
