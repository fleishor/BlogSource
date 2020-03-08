---
title: Install Docker under OpenSuse
date: 2019-12-25 11:13:51
tags: 
- install 
- docker 
- opensuse
categories: 
- docker 
- opensuse
x_image_left: baumstamm.jpg
---

## Install the docker and docker-compose

```bash
> zypper install docker docker-compose
```

## Start the docker daemon during boot

```bash
> sudo systemctl enable docker
```

## Add current user to docker group and relogin

```bash
> sudo usermod -G docker -a $USER
```

When you start `docker` command it tries to connect to `/var/run/docker.sock` in order to communicate with docker daemon process

```bash
> ll /var/run/docker.sock
> srw-rw---- 1 root docker 0 25. Dez 10:28 /var/run/docker.sock
```

By default only root (necessary for docker daemon) and group docker have read/write access.

## Restart the docker daemon

```bash
> sudo systemctl restart docker
```

## Verify docker is running

```bash
> docker version
```

or

```bash
> docker info
```

## Pull down and run the "Hello World" docker container from dockerhub

```bash
> docker run hello-world
```

`docker run` always creates a new container; `docker ps -a` shows all containers

## Show all containers

```bash
docker ps -a
```

## Start container

```bash
docker start {ID from docker ps -a} -a
```

## Remove container

```bash
docker rm {ID from docker ps -a}
```

## Show all images

```bash
docker images
```

## Remove image

```bash
docker rmi {ID from docker images}
```

