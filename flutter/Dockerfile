FROM debian:buster

# Install prerequisites
RUN apt-get update && apt-get install -y sudo curl git unzip xz-utils zip libglu1-mesa wget default-jre

# Set ENV
ENV FLUTTER_VERSION 1.22.1-stable
ENV NODE_VERSION 14
ENV ANDROID_SDK_VERSION 29
ENV ANDROID_SDK_ROOT /opt/android
ENV PATH "$PATH:/opt/flutter/bin"

# Set working dir
WORKDIR /opt
RUN mkdir -p android

# Install NodeJS
RUN curl -sL https://deb.nodesource.com/setup_${NODE_VERSION}.x | sudo bash -
RUN apt install -y nodejs

# Install firebase-cli
RUN npm install -g firebase-tools

# Download Android SDK
RUN wget https://dl.google.com/android/repository/commandlinetools-linux-6200805_latest.zip

# Setup Android SDK
RUN unzip commandlinetools-*.zip && rm commandlinetools-*.zip
RUN mv tools /opt/android
RUN cd /opt/android/tools/bin && yes | ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} --licenses
RUN cd /opt/android/tools/bin && ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} "build-tools;${ANDROID_SDK_VERSION}.0.3" "patcher;v4" "platform-tools" "platforms;android-${ANDROID_SDK_VERSION}" "sources;android-${ANDROID_SDK_VERSION}"

# Download Flutter SDK
RUN wget -O flutter.tar.xz https://storage.googleapis.com/flutter_infra/releases/stable/linux/flutter_linux_${FLUTTER_VERSION}.tar.xz
RUN tar xfv flutter.tar.xz
RUN rm flutter.tar.xz

# Run basic check to download Dart SDK
RUN flutter doctor

# Check versions
RUN java -version
RUN firebase -V