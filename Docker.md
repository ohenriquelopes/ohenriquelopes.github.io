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

``` Markdown
docker exec -it nginx bash
docker run -d ubuntu _run ubuntu in detach_
docker build <image> _build an image from a docker file_
docker build -t usernamedockerhub/nome:versão local(.)
docker build -t henriquelopes52/nginx-hl:latest .
docker rmi <image> _remove docker image_
docker rm <container_id> _Remove container_
docker pull _pull an image or a repository from a reistry_
docker push  _pushes an image or a repository to a registry_
docker exec _Runs a command in a run-time container_
docker ps  _Show running containers_
docker ps -a _Show all containers_
docker search _Searches the docker hub for images_
docker container prune _Remove all containers_
docker stop -t 0 $(docker ps -q) _Stop all containers_
docker network ls _List networks created_
```


## Dockerfile
``` Markdown
FROM nginx:latest
_FROM image:version_
COPY index.html /usr/share/nginx/html/
_Copia os arquivos index.html para a pasta /html do container_

RUN apt-get update && apt-get install -y vim
_Atualiza os pacotes e instala o VIM_


```

## Docker-compose

``` Markdown
docker-compose up -d
_Sobe o container em modo detach_
```

```Markdown
version: '3'
    nginx: 
        image: henriquelopes52/nginx-hl:latest
        ports:
            - "8080:80"
        volumes:
            - ./nginx/html:/usr/share/nginx/html
```