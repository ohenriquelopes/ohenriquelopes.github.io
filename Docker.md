#Docker CLI

### Docker run

```Markdown
- docker run --rm --name=nginx -p 8080:80 nginx

_--rm (The options tells command to remove the container when it exists automatically)_
_--name (Attribute allows you to assign a container name)_
_-p_ ([host_ip]:[host_port]:[container_port])host_ip element is optional and you don't need to specify it when running the command.
For example, to map TCP port 80 in the container to port 8080 on the Docker host you would run: 8080:80
_-v [/host/volume/location]:[/container/storage]_
```



### Docker exec

```
docker exec -it nginx bash
```