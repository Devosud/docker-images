FROM debian:stretch

# Prerequisites
RUN apt-get update && apt-get install -y curl git unzip xz-utils zip libglu1-mesa wget openjdk-8-jdk

# Check JAVA
RUN java -version

# Set working dir
WORKDIR /opt
RUN mkdir -p android

# Set env
ENV ANDROID_SDK_ROOT /opt/android
ENV PATH "$PATH:/opt/flutter/bin"

# Download Android SDK
RUN wget https://dl.google.com/android/repository/commandlinetools-linux-6200805_latest.zip

# Setup Android SDK
RUN unzip commandlinetools-*.zip && rm commandlinetools-*.zip
RUN mv tools /opt/android
RUN cd /opt/android/tools/bin && yes | ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} --licenses
RUN cd /opt/android/tools/bin && ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} "build-tools;29.0.2" "patcher;v4" "platform-tools" "platforms;android-29" "sources;android-29"

# Download Flutter SDK
RUN git clone https://github.com/flutter/flutter.git

# Run basic check to download Dart SDK
RUN flutter doctor

# Update the SDK if needed
RUN flutter upgrade
