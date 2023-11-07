## Perform system update
sudo apt update

## Install Docker-Compose
sudo apt install docker-compose -y

## Create docker-compose.yml
this yml has all configuration for installing Jenkins.
sudo vi docker-compose.yml 

```
(Copy the below code high-lighted in yellow color)
version: '3'
services:
  jenkins:
    image: jenkins/jenkins:lts
    restart: always
    privileged: true
    user: root
    ports:
      - 8080:8080
      - 50000:50000
    container_name: jenkins
    volumes:
      - /home/ubuntu/jenkins_compose/jenkins_configuration:/var/jenkins_home
      - /var/run/docker.sock:/var/run/docker.sock
```

## Execute Docker compose command:
sudo docker-compose up -d 


## check docker logs
docker logs
a746b233f658429f90efc4862fcec773


## check interface jenkins
127.0.0.1:8080
pass : a746b233f658429f90efc4862fcec773

