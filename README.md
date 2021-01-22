
# Docker Build
* How to make a docker base image, you can start by writing Dockerfile. 
```
    FROM scratch
    MAINTAINER  Fisher "supmacro@foxmail.com"
    ADD  alpine-minirootfs-3.13.0-x86_64.tar.gz /
    CMD  ["/bin/sh"]
```

# Syntax
| command | demo | description | 
|:-- |:-- |:-- |
|


# .dockerignore
Before the docker CLI sends the context to the docker daemon, it looks for a file named .dockerignore 
in the root directory of the context. If this file exists, the CLI modifies the context to exclude 
files and directories that match patterns in it. 
This helps to avoid unnecessarily sending large or sensitive files and directories to the daemon and 
potentially adding them to images using ADD or COPY.

| demo | description |
|:-- |:-- |
| \*/temp\* | Exclude files and directories whose names start with 'temp' in any immediate <br>\
subdirectory of the root. For example, the plain file /somedir/temporary.txt is excluded, as is the directory /somedir/temp


# Note
* How to use GDB in docker?  
In general, in order to protect the security of the host, docker will turn on ASLR (Address space layout randomization) 
by default, that is, the memory address in docker and the host memory address are different. ou can give 
super permission to solve this problem before running docker. 
Not only solves this problem, you can also start docker in docker.
```
/* docker run --privileged -it image:tag */
docker run --cap-add=SYS_PTRACE --security-opt seccomp=unconfined
```

