# Docker Compose

This is the complete demo built using docker-compose. You will need to add your trial certificate and key to the builder directory.

## docker-compose.yml

In this file we again define each service, ports, volumes and custom network. If you notice the proxy service we don't use the default image, we build a customer docker image. `context` points use to the path of our dockerfile and `dockerfile` is our file name, in this case *Dockerfile*.

```
services:
  proxy:
    container_name: nginx_lb
    build:
      context: ./builder
      dockerfile: Dockerfile
    volumes:
      - ./lb_php/:/etc/nginx/conf.d/
    ports: 
      - "8081:80"
    networks:
      docnet:
        ipv4_address: 172.10.1.20
```