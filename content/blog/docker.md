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

* docker image build -t <image name > . 
* docker image push <image name >
* docker service ls
* docker container ls
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

