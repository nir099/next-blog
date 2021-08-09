---
template: blog-post
title: Docker
publishedDate: 2021-08-04T11:25:00.140Z
description: |
  Docker Docker 
featured: false
img: ../../static/images/ian-taylor-hjbombpbi9k-unsplash.jpg
imgAlt: docker
tags:
  - docker
---
#### Docker

* docker system info
* docker image pull <name>:latest 
* docker image ls
* docker image build -t <image name > . 
* docker image build -t <image_name> <git_repo>
* docker image push <image name >
* docker container ls
  - list running containers
* docker container run -it alphine sh 
  - run docker container interactively with shell
  - ctr + P + Q to exit
     - this dose not kill the container
  - running exit cmd kill the container
* docker container ls -a 
  - list all containers
* docker container stop < id >
  - part of id is sufficient 
  - an id looklike 97969385874096298601640864
  - giving 97 is enough
* docker container start < id >
* docker container exec -it < id > sh
* docker swarm init
* docker swarm join
* docker swarm join-token manager
* docker service ls
* docker service ps <name>
* docker service scale <name>=10

  \- \[scale up to 10]
* docker service create --name <name> -p 8080:8080 --replicas 3 <docker image >

  \-  \[ run 3 docker instance of docker image on port 8080 ]
* docker container rm <containerid> <containerId> -f 

  \- \[ for remove specific container | -f for terminate running ones |  then if we have mensioned scale limit it will re-trigger new containers up to the limit ]
* docker service rm <name> 

  \- \[ remove the named service entirely ]



#### Compose

```
version: "3.8"
services:
  web-fe:
    image: nigelpoulton/gsd:swarm-stack
    command: python app.py
    deploy:
      replicas: 10 -- replica limit
    ports:
      - target: 8080 -- open port
        published: 5000
    networks:
      - counter-net
    volumes:
      - type: volume
        source: counter-vol
        target: /code
  redis:
    image: "redis:alpine"
    networks:
      counter-net:

networks:
  counter-net:

volumes:
  counter-vol:
```
* docker stack deploy -c docker-compose.yml <name>
* docker stack ls
* docker stack service <name>
* docker stack ps <name>


