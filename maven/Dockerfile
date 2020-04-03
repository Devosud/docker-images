FROM debian:buster

#Maven options
ENV MAVEN_OPTS="-DskipTests -Dmaven.repo.local=.m2/repository"

#Install Maven
RUN apt-get install maven

#Install Docker
RUN apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
RUN add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"
RUN apt-get update
RUN apt-get install docker-ce docker-ce-cli containerd.io
