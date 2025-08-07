---
date: 2025-03-30
tags:
  - docker
  - devops
---
Commands in the docker file:

- FROM - specifies a base image to use
- ENV - specify environment variables in the container
- RUN - run any shell command in the container. Its a build step of the image. The state of the container after the run command will be committed to the container image. 
- WORKDIR - sets the working directory in the container. So any RUN, COPY, or ADD commands will have the directory as its point. This improves maintainability and is a good practice. 
- COPY - runs on the host. Can copy files from host to the container
- CMD - This is the command that executes when you launch the build image. Can be overridden when starting an image with "docker run $image $other_command". 
- EXPOSE - Expose a port to the outside

Each step in dockerfile is being cached, so it will not get executed again for the image build if nothing is actually changed. 

### References

