---
title: udemy
date: 2024-02-09
resources: 
tags:
---

# Docker Commands

# Run an Image

```cmd
docker run nginx
```

- If image not exist locally, it will install from hub.docker.com
- This command will pull the image remotely and creates a container out of it.

# Pulling an Image

```cmd
docker pull nginx
```

- Just pulling an image but not creating a container out of it.

---
# List Containers

- List of all active containers

```cmd
docker ps
```

- To see all dead containers and running containers.

```cmd
docker ps -a
```

---
# Stop a Container

```cmd
docket ps
docker stop [container name]
docker ps -a
```

---
# Removing a Stopped Container Permanently

- ! Disk cleanup

```cmd
docker rm [name1 name2 name3]/[id1 id2 id3]
```

Return value - name of the container itself

To conform it:

```cmd
docker ps -a
```

---
# List Images

```cmd
docker images
```

## Remove the Image

```cmd
docker rmi nginx
```

---
# CentOS Container

![[Pasted image 20240209231345.png]]

---

![[01-docker-commands.pdf]]

---
