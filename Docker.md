# Docker CLI

### Docker run

```Markdown
- docker run --rm --name=nginx -p 8080:80 nginx

--rm (The options tells command to remove the container when it exists automatically)
--name (Attribute allows you to assign a container name)
-p ([hostip]:[hostport]:[containerport])hostip element is optional and you don't need to specify it when running the command.
For example, to map TCP port 80 in the container to port 8080 on the Docker host you would run: 8080:80
-v [/host/volume/location]:[/container/storage]
```

### Docker commands

``` Markdown
docker exec -it nginx bash
docker run -d ubuntu run ubuntu in detach
docker build <image> build an image from a docker file
docker build -t usernamedockerhub/nome:versão local(.)
docker build -t henriquelopes52/nginx-hl:latest .
docker rmi <image> remove docker image
docker rm <containerid> Remove container
docker pull pull an image or a repository from a reistry
docker push  pushes an image or a repository to a registry
docker exec Runs a command in a run-time container
docker ps  Show running containers
docker ps -a Show all containers
docker search Searches the docker hub for images
docker container prune Remove all containers
docker stop -t 0 $(docker ps -q) Stop all containers
docker network ls List networks created
```

## Dockerfile

``` Markdown
FROM nginx:latest
FROM image:version
COPY index.html /usr/share/nginx/html/
Copia os arquivos index.html para a pasta /html do container

RUN apt-get update && apt-get install -y vim
Atualiza os pacotes e instala o VIM


```

## Docker-compose

``` Markdown
docker-compose up -d
Sobe o container em modo detach
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
