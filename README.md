# docker-training
docker training repo

## commands
| info  | command   |
| ----- | --------- |
| list images  | `docker images` |
| list images with full shaID | `docker images --no-trunc` |
| remove image |  `docker rmi <image-name>`|
| build image from docker file  | `docker build -t <image-name> .` |
| run image | `docker run <image-name>` |
| pull image | `docker pull <image-name>` |
| tag an image | `docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]` |
| cleanup dangling images | `docker images prune` |
| cleanup images,containers,volumes | `docker system prune` |
| kill running containers | `docker kill $(docker ps -q)` |
| delete stopped containers |  `docker rm $(docker ps -a -q)` |
| delete all images | `docker rmi $(docker images -q)` #`-f` forcefully|
| intreact with a container | `docker exec [OPTIONS] CONTAINER COMMAND [ARG...]` |
| docker logs | `docker logs CONTAINER` # `-f`  not to stop/wait|
| list running containers |  `docker ps`|


## Examples

Docker version
```
$ docker --version
Docker version 19.03.1, build 74b1e89
```

First container
```
$ docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

```
Start nginx container

`docker run nginx`

Start Centos server and execute ping

`docker container run centos ping -c 5 127.0.0.1`

start nginx container with port exposed

```docker run -p 80:80 nginx
curl http://localhost:80
```

Adding volumes to container

`docker run -p 80:80 -v /Users/rlokinen/Desktop/Backup/gitrepos/EXTERNAL/docker-training/html/:/usr/share/nginx/html nginx`

Building image from dockerfile

`docker build -t IMAGE:TAG -f Dockerfile-nginx .`

Login to a container
`docker exec -it CONTAINER /bin/bash`


## Tagging and pushing Docker images

```
$ docker tag nginx-test:3.0 raghavendar/docker-training:latest

$ docker push raghavendar/docker-training:latest
The push refers to repository [docker.io/raghavendar/docker-training]
1a8148369769: Preparing 
ccdb13a20bf2: Preparing 
9513cdf4e497: Preparing 
7f083f9454c0: Preparing 
29f36b5893dc: Preparing 
denied: requested access to the resource is denied


LAMU02WJ2MEHTD6:RabbitMQ rlokinen$ docker login
Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Username: raghavendar
Password: 
Login Succeeded

LAMU02WJ2MEHTD6:RabbitMQ rlokinen$ docker push raghavendar/docker-training:latest
The push refers to repository [docker.io/raghavendar/docker-training]
1a8148369769: Pushed 
ccdb13a20bf2: Mounted from library/ubuntu 
9513cdf4e497: Mounted from library/ubuntu 
7f083f9454c0: Mounted from library/ubuntu 
29f36b5893dc: Mounted from library/ubuntu 
latest: digest: sha256:274157d312f0f1e9447b66b8eb40422631ab262361b43d7af9f5e9f692440cc5 size: 1362
```
