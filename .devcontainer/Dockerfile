from mcr.microsoft.com/devcontainers/base:jammy

# # Flutter SDK
# # https://flutter.dev/docs/development/tools/sdk/releases?tab=linux
# ENV FLUTTER_CHANNEL="stable"
# ENV FLUTTER_VERSION="3.3.4"
# # Make sure to use the needed channel and version for this.
# ENV FLUTTER_HOME=~/flutter
# ENV PATH=${PATH}:${FLUTTER_HOME}/bin

# # Flutter SDK
# RUN curl -C - --output flutter.tar.xz https://storage.googleapis.com/flutter_infra_release/releases/${FLUTTER_CHANNEL}/linux/flutter_linux_${FLUTTER_VERSION}-${FLUTTER_CHANNEL}.tar.xz \
# 	&& tar -xf flutter.tar.xz -C ~ \
# 	&& rm flutter.tar.xz \
# 	&& flutter config --android-sdk "${ANDROID_SDK_ROOT}" \
# 	&& yes | flutter doctor --android-licenses \
# 	&& flutter config --no-analytics \
# 	&& flutter update-packages