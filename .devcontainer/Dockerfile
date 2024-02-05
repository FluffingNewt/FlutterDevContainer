from mcr.microsoft.com/devcontainers/base:ubuntu

# ENV USERNAME="vscode"
# ENV USER_UID=1000
# ENV USER_GID=${USER_UID}

ENV USER_HOME=/home/${USERNAME}

# ENV ANDROID_TOOLS_URL="https://dl.google.com/android/repository/commandlinetools-linux-6858069_latest.zip"
# ENV ANDROID_VERSION="29"
# ENV ANDROID_BUILD_TOOLS_VERSION="29.0.3"
# ENV ANDROID_ARCHITECTURE="x86_64"
# ENV ANDROID_SDK_ROOT="$USER_HOME/android"

ENV FLUTTER_HOME="$USER_HOME/sdk/flutter"

# ENV PATH="$ANDROID_SDK_ROOT/cmdline-tools/tools/bin:$ANDROID_SDK_ROOT/emulator:$ANDROID_SDK_ROOT/platform-tools:$ANDROID_SDK_ROOT/platforms:$FLUTTER_HOME/bin:$FLUTTER_USER_CACHE/bin:$PATH"

# Make sure all required packages are installed
RUN apt-get update
RUN apt-get install -y wget \
	xz-utils \
	git \
	curl \
	file \
	unzip \
	zip \
	openjdk-17-jdk-headless --no-install-recommends
	
RUN apt-get autoremove -y \
	&& apt-get clean -y \
	&& rm -rf /var/lib/apt/lists/* 

# Flutter
# RUN git clone -b master https://github.com/flutter/flutter.git ${FLUTTER_HOME}
# RUN ./${FLUTTER_HOME}/bin/flutter --JAVA_VERSION
# ENV PATH="/sdk/flutter/bin:${PATH}"
# RUN chmod -R 777 /sdk/flutter

# USER $USERNAME
# WORKDIR /home/$USERNAME

