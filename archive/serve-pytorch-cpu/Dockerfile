FROM public.ecr.aws/j1r0q0g6/notebooks/notebook-servers/jupyter-pytorch-full:v1.5.0
  
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
RUN pip install torchserve==0.8.1
RUN pip install torch-model-archiver==0.8.1

# install packages
RUN pip install huggingface-hub==0.16.4
RUN pip install boto3==1.28.10
RUN pip install transformers==4.31.0
RUN pip install captum==0.6.0

# add jupyter path into execute path
ENV PATH="$PATH:~/.local/bin"

EXPOSE 8888

ENV SHELL=/bin/bash
ENV NB_PREFIX /

WORKDIR "${HOME}"