FROM public.ecr.aws/j1r0q0g6/notebooks/notebook-servers/jupyter-pytorch-cuda-full:v1.5.0
  
USER root

ENV NB_USER jovyan
ENV NB_UID 1001
ENV NB_PREFIX /
ENV HOME /home/$NB_USER
ENV SHELL /bin/bash

# create user and set required ownership
RUN mkdir -p ${HOME} \
 && chown -R ${NB_USER}:users ${HOME} \
 && chown -R ${NB_USER}:users /usr/local/bin

# upgrade python
RUN apt-get update
RUN add-apt-repository ppa:deadsnakes/ppa
RUN apt-get install python3.9 -y
RUN \
   echo 'alias python=/usr/bin/python3.9"' >> /root/.bashrc && \
   echo 'alias python3=/usr/bin/python3.9"' >> /root/.bashrc && \
   source /root/.bashrc

# install java JDK 11
RUN apt-get update
RUN apt-get install --no-install-recommends -y openjdk-11-jre-headless

# install extra packages for torchserve
RUN pip install torchserve
RUN pip install torch-model-archiver

# install packages
RUN pip install huggingface-hub
RUN pip install boto3
RUN pip install transformers

# add jupyter path into execute path
ENV PATH="$PATH:~/.local/bin"

EXPOSE 8888

ENV SHELL=/bin/bash
ENV NB_PREFIX /

WORKDIR "${HOME}"