#!/bin/bash

# Paperspace Dockerfile for Gradient base image
# Paperspace image is located in Dockerhub registry: paperspace/gradient_base

# ==================================================================
# Module list
# ------------------------------------------------------------------
# python                        3.11.6           (apt)
# pip3                          23.3.1           (apt)
# cuda toolkit                  12.0.0           (apt)
# cudnn                         8.9.7            (apt)
# torch                         2.1.1            (pip)
# torchvision                   0.16.1           (pip)
# torchaudio                    2.1.1            (pip)
# tensorflow                    2.15.0           (pip)
# transformers                  4.35.2           (pip)
# datasets                      2.14.5           (pip)
# peft                          0.6.2            (pip)
# tokenizers                    0.13.3           (pip)
# accelerate                    0.24.1           (pip)
# diffusers                     0.21.4           (pip)
# safetensors                   0.4.0            (pip)
# jupyterlab                    3.6.5            (pip)
# bitsandbytes                  0.41.2           (pip)
# cloudpickle                   2.2.1            (pip)
# scikit-image                  0.21.0           (pip)
# scikit-learn                  1.3.0            (pip)
# matplotlib                    3.7.3            (pip)
# ipywidgets                    8.1.1            (pip)
# cython                        3.0.2            (pip)
# tqdm                          4.66.1           (pip)
# gdown                         4.7.1            (pip)
# xgboost                       1.7.6            (pip)
# pillow                        9.5.0            (pip)
# seaborn                       0.12.2           (pip)
# sqlalchemy                    2.0.21           (pip)
# spacy                         3.6.1            (pip)
# nltk                          3.8.1            (pip)
# boto3                         1.28.51          (pip)
# tabulate                      0.9.0            (pip)
# future                        0.18.3           (pip)
# jsonify                       0.5              (pip)
# opencv-python                 4.8.0.76         (pip)
# pyyaml                        5.4.1            (pip)
# sentence-transformers         2.2.2            (pip)
# wandb                         0.15.10          (pip)
# deepspeed                     0.10.3           (pip)
# cupy-cuda12x                  12.2.0           (pip)
# timm                          0.9.7            (pip)
# omegaconf                     2.3.0            (pip)
# scipy                         1.11.2           (pip)
# gradient                      2.0.6            (pip) 
# attrs                         23.1.0           (pip)
# default-jre                   latest           (apt)
# default-jdk                   latest           (apt)
# nodejs                        20.x latest      (apt)
# jupyter_contrib_nbextensions  0.7.0            (pip)
# jupyterlab-git                0.43.0           (pip)


# ==================================================================
# Initial setup
# ------------------------------------------------------------------
    ARG BASE_IMAGE=paperspace/gradient-base:pt211-tf215-cudatk120-py311-20240202

    FROM ${BASE_IMAGE} as dev-base

    # Set ENV variables
    ENV LANG C.UTF-8
    ENV SHELL=/bin/bash
    ENV DEBIAN_FRONTEND=noninteractive

    ENV APT_INSTALL="apt-get install -y --no-install-recommends"
    ENV PIP_INSTALL="python3 -m pip --no-cache-dir install --upgrade"
    ENV GIT_CLONE="git clone --depth 10"

# ==================================================================
# Installing A1111 & Comfyui Dependency
# ------------------------------------------------------------------

    RUN $PIP_INSTALL \
        GitPython \
        blendmodes \
        clean-fid \
        einops \
        fastapi>=0.90.1 \
        gradio==3.41.2 \
        inflection \
        jsonmerge \
        kornia \
        lark \
        open-clip-torch \
        piexif \
        psutil \
        pytorch_lightning \
        requests \
        resize-right \
        scikit-image>=0.19 \
        tomesd \
        torchdiffeq \
        torchsde \
        aiohttp 

# ==================================================================
# Startup
# ------------------------------------------------------------------

    EXPOSE 8888 6006

    CMD jupyter lab --allow-root --ip=0.0.0.0 --no-browser --ServerApp.trust_xheaders=True --ServerApp.disable_check_xsrf=False --ServerApp.allow_remote_access=True --ServerApp.allow_origin='*' --ServerApp.allow_credentials=True