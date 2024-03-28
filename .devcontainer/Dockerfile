from ubuntu:latest as ubuntu_container

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
     # Linux prerequisites
     curl \
     git \
     xz-utils \
     zip \
     unzip \
     libglu1-mesa \
     # Flutter prerequisites
     clang \
     cmake \
     ninja-build \
     pkg-config \
     libgtk-3-dev \
     # Chrome prerequisites
     wget \
     gpg \
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
ENV PATH=$PATH:$FLUTTER_HOME/bin

# Install flutter
RUN git clone -b master https://github.com/flutter/flutter.git $FLUTTER_HOME \
 && flutter update-packages \
 && flutter config --enable-web \
 && flutter config --android-sdk "$ANDROID_HOME"

######################################################################################
#################################### Extra Credit ####################################
######################################################################################

# Android SDK

ENV ANDROID_HOME="$HOME/sdk/android"
ENV PATH=$PATH:$ANDROID_HOME/cmdline-tools/latest/bin:$ANDROID_HOME/emulator:$ANDROID_HOME/platform-tools:$ANDROID_HOME/platforms

# Install Android SDK
RUN mkdir -p $ANDROID_HOME \
 && curl -o android_tools.zip https://dl.google.com/android/repository/commandlinetools-linux-11076708_latest.zip \
 && unzip -q -d "$ANDROID_HOME" android_tools.zip \
 && rm android_tools.zip

# Configure SDK files
RUN touch $ANDROID_HOME/repositories.cfg \
 && mkdir $ANDROID_HOME/cmdline-tools/latest \
 && mv $ANDROID_HOME/cmdline-tools/lib $ANDROID_HOME/cmdline-tools/latest \
 && mv $ANDROID_HOME/cmdline-tools/bin $ANDROID_HOME/cmdline-tools/latest \
 && mv $ANDROID_HOME/cmdline-tools/NOTICE.txt $ANDROID_HOME/cmdline-tools/latest \
 && mv $ANDROID_HOME/cmdline-tools/source.properties $ANDROID_HOME/cmdline-tools/latest

# Install and accept Android packages
RUN yes | sdkmanager "platforms;android-34" \
 && yes | sdkmanager "build-tools;34.0.0" \
 && yes | sdkmanager "platform-tools" \
 && yes | sdkmanager "emulator" \
 && yes | sdkmanager "system-images;android-34;google_apis_playstore;x86_64" \
 && sdkmanager --update \
 && yes | sdkmanager --licenses

######################################################################################

# Chrome

RUN sudo wget https://dl-ssl.google.com/linux/linux_signing_key.pub -O /tmp/google.pub \
 && sudo gpg --no-default-keyring \
        --keyring /etc/apt/keyrings/google-chrome.gpg \
        --import /tmp/google.pub \
 && echo 'deb [arch=amd64 signed-by=/etc/apt/keyrings/google-chrome.gpg] http://dl.google.com/linux/chrome/deb/ stable main' | sudo tee /etc/apt/sources.list.d/google-chrome.list \
 && sudo apt update && sudo apt install -y google-chrome-stable \
 && sudo apt autoremove -y \
 && sudo apt clean -y \
 && sudo rm -rf /var/lib/apt/lists/* 

######################################################################################