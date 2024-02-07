from mcr.microsoft.com/devcontainers/base:ubuntu


# RUN export HOME="/home/vscode"
ENV HOME="/home/vscode"
ENV FLUTTER_HOME="${HOME}/sdk/flutter"

ENV PATH=${PATH}:${FLUTTER_HOME}/bin

# Make sure all required packages are installed
RUN  apt update \
    && apt install -y sudo \
    && apt install -y openjdk-17-jdk-headless --no-install-recommends \
    && apt install -y wget curl git clang cmake ninja-build libgtk-3-dev pkg-config xz-utils zip unzip --no-install-recommends \

    # Clean Up
    && apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/* 

# Flutter
RUN mkdir "${HOME}/sdk" \
    && git clone -b master https://github.com/flutter/flutter.git ${FLUTTER_HOME}
