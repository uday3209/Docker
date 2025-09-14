# Docker
Repository for Docker installations and managing images
```
yum install docker -y
systemctl restart docker
systemctl enable docker
```

#### Usecase - 1
Create an container that runs apache application in an ubuntu os using Dockerfile
<br>
### Solution
```
FROM ubuntu:latest

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update && apt install -y apache2 && apt clean

EXPOSE 80

CMD ["apachectl", "-D", "FOREGROUND"]
```

```
docker build -t apache_custom:latest .
docker run -itd --name apacheContainer -p 8080:80 apache_app
```

Check the app using:
```
curl http://localhost:8080
```

#### Usecase - 1
Create an container that runs nginx application with updated index.html file using Dockerfile
<br>
### Solution
```
FROM nginx:latest

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```

docker build -t nginx_app .
docker tag nginx_app nginx_app:v1

docker run -d --name nginx_container1 -p 8080:80 nginx_app:v1

## MONITORING AND MANAGING DOCKER CONTAINER FOR LIFECYCLE

To start a container
```
docker container start <container_name>
```

To get details of a container
```
docker inspect <container_name>
```

To check logs for troubleshooting or identifying issues
```
docker logs <container_name>
```

To monitor real-time resources usage of all running containers
```
docker stats
```

For specific container
```
docker stats <container_name>
```

