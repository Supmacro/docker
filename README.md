
# Docker Build
* How to make a docker base image, you can start by writing Dockerfile. 
```
    FROM scratch
    MAINTAINER  Fisher "supmacro@foxmail.com"
    ADD  alpine-minirootfs-3.13.0-x86_64.tar.gz /
    CMD  ["/bin/sh"]
```

# Note
* How to use GDB in docker?  
In general, in order to protect the security of the host, docker will turn on ASLR 
(Address space layout randomization) by default, that is, the memory address in 
docker and the host memory address are different. ou can give super permission to 
solve this problem before running docker. Not only solves this problem, you can also 
start docker in docker.
```
docker run --privileged -it image:tag
```  
In addition, there is a way to solve this problem.
```
docker run --cap-add=SYS_PTRACE --security-opt seccomp=unconfined
```

