+++
title = "Docker Cheatsheet"
+++
### Docker basics

```
docker start <CONTAINER> #start container
docker restart <CONTAINER> #restart container
docker stop <CONTAINER> #stop container
docker rm <CONTAINER> #remove a container
```

### Listing containers

```
docker ps       #list running containers
docker ps -a    #list all containers
docker ps -s    #list running containers with system specs
```

### Image management

```
docker images       #list local stored images
docker rmi <IMAGE>  #remove a local image
docker save -o <TARBALL> <IMAGE> #Save a local image as a tarball so you can archive or inspect the image.
docker history <IMAGE> #Shows image creation history
```

### Building Images

```
docker build .
docker build --build-arg ARG=VALUE . # pass variables with build arg
```

### Networks

```
docker network ls      # shows docker network info
docker network rm <NETWORKID> #Remove a network using the ID
```
