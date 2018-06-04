docker.md

Lets try to remember some docker commands!

**Build image/ dockerfile**: `$ docker build -t <imagename> .`
* Only run once you have a Dockerfile

**List Docker Images**: `$ docker image ls`

**Example Dockerfile for Go**
```
FROM golang:latest 
RUN mkdir /app 
ADD . /app/ 
WORKDIR /app 
RUN go build -o main . 
CMD ["/app/main"]
```
**Map directory from Docker to local machine**
```$ docker run -v /my/own/datadir:/docker/data/dir <my image>```

**Run bash command on built container**
```$ docker inspect <container name> | grep IPAddress``` this will run `grep IPAddress` on the container, returning the IP Address.
