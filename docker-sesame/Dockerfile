FROM ubuntu:22.04 

# Install dependencies
RUN apt-get update && apt-get install -y curl zip unzip git openjdk-8-jdk
    
# Fix certificate issues
RUN apt-get update && \
    apt-get install ca-certificates-java && \
    apt-get clean && \
    update-ca-certificates -f;

# Setup JAVA_HOME -- useful for docker commandline
ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64/
RUN export JAVA_HOME

# Install sdkman for other dependencies management
RUN curl -s "https://get.sdkman.io" | bash

# This SHELL command is needed to allow using source
SHELL ["/bin/bash", "-c"]    

# You need to put 'sdk install...'' lines in same RUN command as 'source...'.
RUN source "/root/.sdkman/bin/sdkman-init.sh"   \
                && sdk install gradle 6.6       \
                && sdk install groovy 3.0.0


COPY miningframework /home/miningframework

WORKDIR /home/miningframework

