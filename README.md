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
