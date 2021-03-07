FROM ubuntu:18.04
COPY ./app.py train.py request.py requirements.txt docker docker-compose.yml Dockerfile ./

Run pip install -r requirements.txt &&\
    python train.py &&\
    apt update &&\
    apt upgrade &&\
    apt -y  install apt-transport-https ca-certificates curl software-properties-common &&\
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add - &&\
    add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" &&\
    apt update &&\
    apt-cache policy docker-ce &&\
    apt -y install docker-ce &&\
    curl -L "https://github.com/docker/compose/releases/download/1.26.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose &&\
    chmod +x /usr/local/bin/docker-compose &&\
    docker-compose --version &&\
    usermod -a -G docker "$(whoami)" &&\
    newgrp docker &&\
    service --status-all &&\
    service docker start &&\
    docker-compose ps &&\
    sudo rm -rf /usr/share/dotnet &&\
    sudo rm -rf /opt/ghc &&\
    sudo rm -rf "/usr/local/share/boost" &&\
    sudo rm -rf "$AGENT_TOOLSDIRECTORY" &&\
    docker-compose -f docker-compose.yml up -d  &&\
    docker ps -a  &&\
    docker-compose -f docker-compose.yml up -d  &&\
    docker ps -a  &&\
    chmod +x ./run.sh  &&\
    #./run.sh
    python app.py  &&\
    python request.py  &&\
      
