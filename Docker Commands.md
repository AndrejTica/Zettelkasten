---
date: 2025-03-04
tags:
  - docker
---
Build image: 
```
docker build -t my-image-name .
```
-t: the name flag
dockerfile must be in the current dir.

Run image:
```
docker run -d --name my-container-name my-image-name
```
-d: runs the container in backround (detached mode)
--name: assignes a name to the container

List all stopped and running containers
```
docker ps -a
```
-a: lists all containers, including the stopped ones. 

View logs of a running container in real time:
```
docker logs -f my-container-name
```
-f: flag to log in real time (follow)

Stop a running container:
```
docker stop my-container-name
```

Force stop if needed
```
docker kill my-container-name
```

Remove the docker image:
```
docker rmi my-docker-image-name
```

If the image is used by a container, remove the container first:
```
docker rm my-docker-image-name
```

Remove all stoped containers and unused images
```
docker system prune -a
```
-a: A flag to remove all

List all docker images:
```
docker images
```

Get docker container IP:
```
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container_name_or_id
```

Login to a remote artifactory:
```
echo "$EDM_ADMIN_PWD" | docker login --username ${EDM_ADMIN_USER} --password-stdin docker.porscheinformatik.com
```

Tag a docker container
```
docker tag testing-image:latest artifactory.porscheinformatik.com/docker-all/edm/testing-image:latest
```

### References

