from mcr.microsoft.com/devcontainers/base:ubuntu

# ENV LANG C.UTF-8

# ENV USERNAME="vscode"
# ENV USER_UID=1000
# ENV USER_GID=${USER_UID}
# ENV USER_HOME=/home/${USERNAME}

# ENV JAVA_VERSION="17"

# ENV ANDROID_TOOLS_URL="https://dl.google.com/android/repository/commandlinetools-linux-6858069_latest.zip"
# ENV ANDROID_VERSION="29"
# ENV ANDROID_BUILD_TOOLS_VERSION="29.0.3"
# ENV ANDROID_ARCHITECTURE="x86_64"
# ENV ANDROID_SDK_ROOT="$USER_HOME/android"

# ENV FLUTTER_CHANNEL="stable"
# ENV FLUTTER_VERSION="2.2.1"
# ENV FLUTTER_URL="https://storage.googleapis.com/flutter_infra/releases/$FLUTTER_CHANNEL/linux/flutter_linux_$FLUTTER_VERSION-$FLUTTER_CHANNEL.tar.xz"
# ENV FLUTTER_HOME="$USER_HOME/flutter"
# ENV FLUTTER_USER_CACHE="$USER_HOME/.pub-cache"
# ENV FLUTTER_WEB_PORT="8090"
# ENV FLUTTER_DEBUG_PORT="42000"
# ENV FLUTTER_EMULATOR_NAME="flutter_emulator"

# ENV PATH="$ANDROID_SDK_ROOT/cmdline-tools/tools/bin:$ANDROID_SDK_ROOT/emulator:$ANDROID_SDK_ROOT/platform-tools:$ANDROID_SDK_ROOT/platforms:$FLUTTER_HOME/bin:$FLUTTER_USER_CACHE/bin:$PATH"

# Make sure all required packages are installed
RUN  apt update \
	&& apt install -y sudo \
	&& apt install -y openjdk-11-jdk-headless --no-install-recommends \
	&& apt install -y wget curl git xz-utils zip unzip --no-install-recommends \
	&& apt-get autoremove -y \
	&& apt-get clean -y \
	&& rm -rf /var/lib/apt/lists/* 

# USER $USERNAME
# WORKDIR /home/$USERNAME

