---
title: udemy
date: 2024-02-09
resources: 
tags:
---
# Docker commands

# run an image

```cmd
docker run nginx
```

- If image not exist locally, it will install from hub.docker.com

---
# List containers

```cmd
docker ps
```

- To see all containers running or not

```cmd
docker ps -a
```

---
# Stop a container

```cmd
docket ps
docker stop [container name]
docker ps -a
```

---
# Removing a stopped container permanently

```cmd
docker rm silly_sammet
```

Return value - name of the container itself

To conform it:

```cmd
docker ps -a
```

---
# List images

```cmd
docker images
```

## Remove the image

```cmd
docker rmi nginx
```

---
# CentOS container

![[Pasted image 20240209231345.png]]