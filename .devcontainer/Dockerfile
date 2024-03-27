from ubuntu:latest

######################################################################################

# Set up Environmental Variables
ENV DEBIAN_FRONTEND noninteractive
ENV USER="vscode"
ENV HOME="/home/$USER"

# Update packages, install required tools, and clean up
RUN apt update -y \
 && apt install -y \
      sudo \
      openjdk-17-jdk-headless \
      curl \
      git \
      xz-utils \
      zip \
      unzip \
      libglu1-mesa \
      clang \
      cmake \
      ninja-build \
      pkg-config \
      libgtk-3-dev \
      # gnupg \
 && apt autoremove -y \
 && apt clean -y \
 && rm -rf /var/lib/apt/lists/* 

# Create a non-root user and configure sudo for non-password access
RUN useradd -rm -d /home/$USER -s /bin/bash -g root -G sudo -u 1001 $USER \
 && echo $USER ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USER \
 && chmod 0440 /etc/sudoers.d/$USER

USER $USER
WORKDIR $HOME

######################################################################################

# Flutter

ENV FLUTTER_HOME="$HOME/sdk/flutter"
ENV PATH=${PATH}:${FLUTTER_HOME}/bin

RUN git clone -b master https://github.com/flutter/flutter.git ${FLUTTER_HOME} \
 && flutter update-packages \
 && flutter config --enable-web \
 && flutter config --android-sdk "${ANDROID_HOME}"
 # && flutter doctor --android-licenses

######################################################################################
#################################### Extra Credit ####################################
######################################################################################

# Android SDK

ENV ANDROID_HOME="${HOME}/sdk/android"
# ENV PATH=${PATH}:${ANDROID_HOME}/cmdline-tools/latest/bin:${ANDROID_HOME}/emulator:${ANDROID_HOME}/platform-tools:${ANDROID_HOME}/platforms

# ENV ANDROID_VERSION="34"
# ENV ANDROID_BUILD_TOOLS_VERSION="34.0.0"
# ENV ANDROID_ARCHITECTURE="x86_64"

# RUN mkdir ${ANDROID_HOME} \
#   && touch ${ANDROID_HOME}/repositories.cfg \
#   && curl -o android_tools.zip https://dl.google.com/android/repository/commandlinetools-linux-11076708_latest.zip \
#   && unzip -qq -d "${ANDROID_HOME}" android_tools.zip \
#   && rm android_tools.zip \
#   && mkdir ${ANDROID_HOME}/cmdline-tools/latest \
#   && mv ${ANDROID_HOME}/cmdline-tools/bin ${ANDROID_HOME}/cmdline-tools/latest \
#   && mv ${ANDROID_HOME}/cmdline-tools/lib ${ANDROID_HOME}/cmdline-tools/latest \
#   && mv ${ANDROID_HOME}/cmdline-tools/NOTICE.txt ${ANDROID_HOME}/cmdline-tools/latest \
#   && mv ${ANDROID_HOME}/cmdline-tools/source.properties ${ANDROID_HOME}/cmdline-tools/latest \
#   && yes "y" | sdkmanager "build-tools" \
#   && yes "y" | sdkmanager "platforms" \
#   && yes "y" | sdkmanager "platform-tools" \
#   && yes "y" | sdkmanager "emulator" \
#   && yes "y" | sdkmanager "system-images;google_apis_playstore" \
#   && yes "y" | sdkmanager --licenses

######################################################################################

# Chrome

# RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
#   && echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list \
#   && apt-get update \
#   && apt-get install -y google-chrome-stable \
#   && rm -rf /var/lib/apt/lists/*

######################################################################################