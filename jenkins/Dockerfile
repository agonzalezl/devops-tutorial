FROM jenkins/jenkins:2.316

#Please, don't leave this at root in production
USER root

RUN apt-get update
RUN apt-get -y --no-install-recommends install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

RUN curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

RUN echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null

RUN apt-get update 
RUN apt-get -y --no-install-recommends install docker-ce docker-ce-cli containerd.io

# Remeber to go back to jenkins user in production environments
#USER jenkins