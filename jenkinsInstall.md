***************************
# Steps to Deploy Jenkins With Docker
## 1. Create a folder on your mac/instance (Docker/jenkins):
- this folder will be use for your custom files.
- Use another data folder for persistance storage.

## 2. Add storage path to Dockerfile: 
- pwd in the data storage directory and copy the path and add it to the code or command below.
- Your path /Users/ignatiusn/Docker/data: and then the Jenkins path /var/jenkins_home
- Example: /Users/ignatiusn/Docker/data:/var/jenkins_home

## 3. Create a network and add it on the command:
- $ docker network create jenkins_network
- $ docker network ls

## 4. Docker Compose Code:
- You don't need step 5 if you use this.
- Create folder & Make sure you change the volume path:
```
version: '3.8'

services:
  jenkins01:
    image: jenkins/jenkins
    container_name: jenkins01
    ports:
      - "8080:8080"
      - "50000:50000"
    networks:
      - jenkins_network
    volumes:
      - /Users/ignatiusn/Docker/data:/var/jenkins_home

networks:
  jenkins_network:
    driver: bridge
```
## 5. Deploy con by using below CMD or Use Docker Compose:
```
docker run -itd --name jenkins01 -p 8080:8080 -p 50000:50000 --network jenkins01 -v /Users/ignatiusngwaabanjong/Docker/data:/var/jenkins_home jenkins/jenkins
```

## 6 Browse app:
- Check the logs on Docker Desktop and copy the password, also click 8080 or use below URL.
http://localhost:8080/
Password: 01cbba226a5e448bbcc57326d1d8f9c7

## 7. Install the dependencies and create login.
- USERNAME: admin
- PASSWORD: admin123

COMMANDS:
```
docker compose up -d 
docker compose down
docker compose start
docker compose stop
```
*****************************
