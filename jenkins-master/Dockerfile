FROM jenkins/jenkins:2.319.1-jdk11
USER root
RUN apt-get update && apt-get install -y lsb-release
RUN curl -fsSLo /usr/share/keyrings/docker-archive-keyring.asc \
  https://download.docker.com/linux/debian/gpg
RUN echo "deb [arch=$(dpkg --print-architecture) \
  signed-by=/usr/share/keyrings/docker-archive-keyring.asc] \
  https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list
#Install AWS CLI ver 1 using pip
RUN apt-get update && apt-get install -y docker-ce-cli && apt install python3-pip -y && pip install awscli==1.15.19 

#Install AWS CLI ver 2
# RUN apt-get update && \
#     apt-get install -y \
#         unzip \
#         curl \
#     && apt-get clean \
#     && curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
#     && unzip awscliv2.zip \
#     && ./aws/install \
#     && rm -rf \
#         awscliv2.zip \
#     && apt-get -y purge curl \
#     && apt-get -y purge unzip 

RUN echo "Australia/Melbourne" > /etc/timezone
USER jenkins
#RUN jenkins-plugin-cli --plugins "blueocean:1.25.2 docker-workflow:1.26"