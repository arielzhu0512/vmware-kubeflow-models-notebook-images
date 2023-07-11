FROM public.ecr.aws/j1r0q0g6/notebooks/notebook-servers/jupyter-pytorch-cuda:v1.5.0
  
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
RUN python3.9
RUN update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.9 1
RUN update-alternatives --set python3 /usr/bin/python3.9

# Install notebook
RUN pip install pip
RUN pip install ipykernel notebook jupyterlab

# install - requirements.txt
COPY --chown=jovyan:users requirements.txt /tmp/requirements.txt
RUN python3 -m pip install -r /tmp/requirements.txt --quiet --no-cache-dir \
 && rm -f /tmp/requirements.txt

# install packages
RUN pip install transformers
RUN pip install accelerate
RUN pip install gradio
RUN pip install sentencepiece

# add jupyter path into execute path
ENV PATH="$PATH:~/.local/bin"

EXPOSE 8888

ENV SHELL=/bin/bash
ENV NB_PREFIX /

WORKDIR "${HOME}"