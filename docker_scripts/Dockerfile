FROM jenkins/jenkins:lts-jdk11
USER root
RUN apt-get update && apt-get install -y lsb-release wget
RUN curl -fsSLo /usr/share/keyrings/docker-archive-keyring.asc \
    https://download.docker.com/linux/debian/gpg
RUN echo "deb [arch=$(dpkg --print-architecture) \
    signed-by=/usr/share/keyrings/docker-archive-keyring.asc] \
    https://download.docker.com/linux/debian \
    $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list
RUN apt-get update && apt-get install -y docker-ce-cli
RUN export DOCKERTLS_CERTDIR=/certs
RUN export UBUNTU_CODENAME=jammy
RUN apt-get update && apt-get install -y gpg
RUN apt-get update && apt-get install -y ansible
RUN apt-get update && apt-get install -y maven

# USER jenkins
RUN jenkins-plugin-cli --plugins "nexus-artifact-uploader:2.14 ansible:303.vccb_73a_956ecd artifactory:4.0.0"
