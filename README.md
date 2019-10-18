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
