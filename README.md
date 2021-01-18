
# Docker Build
* This just is a note:
    > How to write a docker base image? 
    > 
    
* Such as:
    ```
    FROM scratch
    MAINTAINER  Fisher "supmacro@foxmail.com"
    ADD  alpine-minirootfs-3.13.0-x86_64.tar.gz /
    CMD  ["/bin/sh"]
    ```
