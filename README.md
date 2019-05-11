# Node.js application demo

Nginx, Node.js and Redis Dockerfiles are based on msanand's code at [https://github.com/msanand/docker-workflow](https://github.com/msanand/docker-workflow).

## Start services

Edit config.toml, change _BackendOverrideAddress_'s value to the IP of the host running the app.

```bash
docker-compose up -d

docker-compose scale node=5
```

## Build containers manually

```bash
docker build -t nvbeta/nginx ./nginx
docker build -t nvbeta/node ./node
```
