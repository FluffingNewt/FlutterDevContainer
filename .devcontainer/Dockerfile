from mcr.microsoft.com/devcontainers/base:ubuntu

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=${USER_UID}

ENV HOME=/home/${USERNAME}

# Make sure all required packages are installed
RUN apt update \
	&& apt install -y sudo \
	&& apt install -y openjdk-17-jdk-headless --no-install-recommends \
	&& apt install -y wget curl git xz-utils zip unzip --no-install-recommends 

# RUN apt-get install -y wget \
#     bash \
#     curl \
#     file \
#     git \
#     mkdir \
#     rm \
#     which \
#     xz-utils \
#     zip \
#     unzip \
#     openjdk-17-jdk-headless --no-install-recommends \
#     ninja-build \
#     clang \
#     cmake \
#     pkg-config

# RUN apt-get autoremove -y \
#     && apt-get clean -y \
#     && rm -rf /var/lib/aot/list/*

