FROM ubuntu:latest
ARG DEBIAN_FRONTEND=noninteractive

WORKDIR /var/flutter

RUN apt-get update && apt-get upgrade -y && \
    apt-get install -y curl git unzip xz-utils && \
    rm -rf /var/lib/apt/lists/*

# Set up Flutter environment variables
ENV FLUTTER_HOME=/flutter
ENV PATH=$FLUTTER_HOME/bin:$PATH

# Download and install Flutter
RUN git clone https://github.com/flutter/flutter.git $FLUTTER_HOME && \
    $FLUTTER_HOME/bin/flutter --version

# Run Flutter doctor to ensure all dependencies are met
RUN $FLUTTER_HOME/bin/flutter doctor

COPY ./data/ .
RUN chmod +x /var/flutter/main.sh
CMD /var/flutter/main.sh

# implemt this below code for particular flutter version 

# ARG FLUTTER_VERSION=2.8.0
# # Download and install Flutter specific version
# RUN git clone https://github.com/flutter/flutter.git $FLUTTER_HOME && \
#     cd $FLUTTER_HOME && \
#     git checkout tags/$FLUTTER_VERSION && \
#     $FLUTTER_HOME/bin/flutter --version
