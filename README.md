
# Docker Build
* How to make a docker base image, you can start by writing Dockerfile. 
```
    FROM scratch
    MAINTAINER  Fisher "supmacro@foxmail.com"
    ADD  alpine-minirootfs-3.13.0-x86_64.tar.gz /
    CMD  ["/bin/sh"]
    LABLE Author="WP.Zhou" Image="centos:8.3.epel"
    EXPOSE 8080/udp
    ENV LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
```


# Syntax
| command | description | 
|:-- |:-- |
| FROM | Specify the base image |
| MAINTAINER | Maintainer information |
| RUN | The RUN instruction will execute any commands in a new layer on top of the<br> current image and commit the results |
| CMD | The main purpose of a CMD is to provide defaults for an executing container. |  
| LABEL | The LABEL instruction adds metadata to an image. use 'docker image inspect IMAGE:TAG' show label |
| EXPOSE | Container listens on the specified network ports at runtime | 
| ENV | The ENV instruction sets the environment variable 'key' to the value 'value' |
| ADD | The ADD instruction copies new files, and adds them to the filesystem of the image at the path |
| ENTRYPOINT | Often used to set the first command after the container is started |
| WORKDIR | The WORKDIR instruction sets the working directory for other instructions that follow it in the Dockerfile |
| ARG | The ARG instruction defines a variable, you can use with "--build-arg 'varname'='value'" |
| ONBUILD | The ONBUILD instruction adds to the image a trigger instruction to be executed at a later time |
| STOPSIGNAL | The STOPSIGNAL instruction sets the system call signal that will be sent to the container to exit. |


## Note
* When starting the container, the commands given by'docker run \*' and'CMD \*' can only be used as additional 
parameters of ENTRYPOINT.
* Environment variables defined using the ENV instruction always override an ARG instruction of the same name.



# .dockerignore
Before the docker CLI sends the context to the docker daemon, it looks for a file named .dockerignore 
in the root directory of the context. If this file exists, the CLI modifies the context to exclude 
files and directories that match patterns in it. 
This helps to avoid unnecessarily sending large or sensitive files and directories to the daemon and 
potentially adding them to images using ADD or COPY.

| demo | description |
|:-- |:-- |
| \*/temp\* | Exclude files and directories whose names start with 'temp' in the root. |
| temp? | Exclude files and directories whose names are a one-character extension of temp. |
| \*\* | \*\* that matches any number of directories (including zero) |
| ! | Lines starting with ! (exclamation mark) can be used to make exceptions to exclusions. |


# Notebook
* How to use GDB in docker?  
In general, in order to protect the security of the host, docker will turn on ASLR (Address space layout randomization) 
by default, that is, the memory address in docker and the host memory address are different. ou can give 
super permission to solve this problem before running docker. 
Not only solves this problem, you can also start docker in docker.
```
/* docker run --privileged -it image:tag */
docker run --cap-add=SYS_PTRACE --security-opt seccomp=unconfined
```


# Reference 
https://docs.docker.com/engine/reference/builder/#dockerignore-file


