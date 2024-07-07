# Use the official Gradle image as a base
FROM gradle:7.6.0-jdk11

# Install dependencies
RUN apt-get update && apt-get install -y wget unzip

# Install Android SDK
RUN mkdir -p /usr/local/android-sdk-linux/cmdline-tools && cd /usr/local/android-sdk-linux/cmdline-tools \
    && wget https://dl.google.com/android/repository/commandlinetools-linux-8512546_latest.zip \
    && unzip commandlinetools-linux-8512546_latest.zip -d tools \
    && mv tools /usr/local/android-sdk-linux/cmdline-tools/latest

# Set environment variables
ENV ANDROID_HOME /usr/local/android-sdk-linux
ENV PATH $ANDROID_HOME/cmdline-tools/latest/bin:$ANDROID_HOME/platform-tools:$PATH

# Accept licenses
RUN mkdir -p ~/.android && touch ~/.android/repositories.cfg
RUN yes | sdkmanager --sdk_root=$ANDROID_HOME --licenses

# Install essential SDK components
RUN sdkmanager --sdk_root=$ANDROID_HOME "platform-tools" "platforms;android-30" "build-tools;30.0.3"

# Set the working directory
WORKDIR /home/gradle/project

# Copy the necessary files and directories into the container
COPY . .

# Run the Gradle build command
CMD ["gradle", "build"]
