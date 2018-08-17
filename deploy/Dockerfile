# Use an official cuda runtime as a parent image
FROM nvidia/cuda:9.0-cudnn7-devel-ubuntu16.04

# Set the working directory to /app
WORKDIR /app

# Install base dependencies
RUN apt update && apt install -y \
        curl \
        wget \
        git \
        tree \
        vim \
        locales \
        python3-pip \
        python3-dev \
        software-properties-common \
        libgeos-dev


# Install python 3.6/3.7 and pipenv
RUN add-apt-repository ppa:deadsnakes/ppa && \
    apt update && \
    apt install -y python3.6 python3.6-tk python3.6-dev && \
    apt install -y python3.7 python3.7-tk python3.7-dev && \
    pip3 install pipenv

# Updates ENV
RUN locale-gen en_US.UTF-8
ENV LC_ALL=en_US.UTF-8
ENV LANG=en_US.UTF-8
ENV LANGUAGE=en_US.UTF-8
ENV SHELL=/bin/bash

COPY ./Pipfile /base/Pipfile
RUN cd /base && pipenv install

COPY ./Makefile /base/Makefile
WORKDIR /base/
