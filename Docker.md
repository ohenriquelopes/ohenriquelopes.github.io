# Docker CLI

### Docker run

```Markdown
- docker run --rm --name=nginx -p 8080:80 nginx

_--rm (The options tells command to remove the container when it exists automatically)_
_--name (Attribute allows you to assign a container name)_
_-p_ ([host_ip]:[host_port]:[container_port])host_ip element is optional and you don't need to specify it when running the command.
For example, to map TCP port 80 in the container to port 8080 on the Docker host you would run: 8080:80
_-v [/host/volume/location]:[/container/storage]_
```



### Docker commands

```
docker exec -it nginx bash
docker run -d ubuntu _run ubuntu in detach_
docker build <image> **build an image from a docker file**
docker rmi <image> _remove docker image_
docker rm <container_id> remove container
docker pull _pull an image or a repository from a reistry_
docker push - pushes an image or a repository to a registry
docker exec _Runs a command in a run-time container_
docker ps - _Show running containers_
docker ps -a _Show all containers_
docker search _Searches the docker hub for images_
docker container prune _Remove all containers_
docker stop -t 0 $(docker ps -q) _Stop all containers_
docker network ls _List networks created_
```


## Dockerfile
```

```

## Docker-compose
```

```