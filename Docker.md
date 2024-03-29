# Docker CLI

### Docker run

```Markdown
- docker run --rm --name=nginx -p 8080:80 nginx

--rm (The options tells command to remove the 
container when it exists automatically)
--name (Attribute allows you to assign a container name)
-p ([hostip]:[hostport]:[containerport])hostip element is optional 
and you don't need to specify it when running the command.
For example, to map TCP port 80 in the container to port 8080 
on the Docker host you would run: 8080:80
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
docker ps -q Only display containers IDs
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

WORKDIR /path/to/workdir



ADD and COPY

ADD or COPY hello* /destination-dir/
Add multiple files with name starting with hello



|                                   | Docker Copy | Docker add |
|-----------------------------------|-------------|------------|
| Is command syntax same            | YES         | YES        |
| Copy multiple files               | YES         | YES        |
| Copy multiples files in one layer | YES         | YES        |
| Copy files from URL               | NO          | YES        |
| Copy archive file (.gz, .tar)     | NO          | YES        |

EXPOSE 80/tcp
EXPOSE 80/udp
By default, expose assumes TCP, You can also specify UDP

CMD ["echo", "hello"]
O CMD pode ser substituido se você rodar algo na linha do docker run, ex:. docker run --rm henrique/hello ola
O resultado vai ser ola

ENTRYPOINT ["echo", "hello"]
O Entrypoint é fixo, se executar o mesmo comando de cima, ele retornar hello ola

ENV <key>=<value>
ENV MY_NAME="Henrique"
ENV MY_DOG="Rez \ the\ Dog
The instruction sets the environment variable to the value.

```

## Docker-compose

``` Markdown
docker-compose up -d
Sobe o container em modo detach
docker-compose down
Destroi todos os containers listados no compose
```

```Markdown
//versao do compose
version: '3'
    //nome do 'objeto'
    nginx: 
    
        image: henriquelopes52/nginx-hl:latest
        ports:
            - "8080:80"
        volumes:
            - ./nginx/html:/usr/share/nginx/html

    mysql:
        image: mysql:5.7
        ports:
            - "3306:3306"
        environment:
            //variavel de ambiente
            - MYSQL_ROOT_PASSWORD=root
            //base de dados
            - MYSQL_DATABASE=test
        volumes:
            - ./data:/var/lib/mysql

    rabbitmq:
        image: rabbitmq:3-management
        ports:
            - "15672:15672"
            - "5672:5672"
        environment:
            - RABBITMQ_DEFAULT_USER=admin
            - RABBITMQ_DEFAULT_PASS=admin
            - RABBITMQ_DEFAULT_VHOST=test
        volumes:
            - ./data-rabbit:var/lib/rabbitmq
```

```markdown
- context: (Compose uses an alternate file to build with. A build path must alse be specifed)
    build:
        context: .
        dockerfile: dockerfile-altenate

- network: (Set thw network containers connect to for the RUN instructions during build)
    build:
        context: .
        network: host

    build:
        context: .
        network: custom_network_1

    build:
        context: .
        network: none

- shm_size ()
    build:
        context: .
        shm_size: '2gb'

    build:
        context: .
        shm_size: 10000000
```

### Redis example docker-compose

```markdown
version: "3.9"
services:
  redis:
    image: redis:latest
    deploy:
      replicas: 1
    configs:
      - my_config
      - my_other_config
configs:
  my_config:
    file: ./my_config.txt
  my_other_config:
    external: true
```
[Link doc docker](https://docs.docker.com/compose/compose-file/compose-file-v3/)