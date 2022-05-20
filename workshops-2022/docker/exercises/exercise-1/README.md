# Exercise 1

## About

Let's run docker containers. Just a simple "Hello".

This is a very simple application in Go. Since docker will load the go environment we need there is no need to install go on your machine.

## Required

- Docker

# Use

Make sure docker is running.

In the root of the exercise-1 directory run the docker command:

`docker build -t hello .`

Let's breakdown the command:

1. `docker` - this lets your machine know you are using docker
2. `build` - this builds an image from a Dockerfile
3. `-t` - Allocate a pseudo-tty
4. `hello` - This is the local directory containing the Go code
5. `.` This is the file(s) to copy from your local directory into the image

We can now see the image in the docker images list.

`docker images`

There will be an images named `hello`

Then to run a container

`docker run -d -p 8080:8080 -t hello`

Your container will be running on port 8080.

Let's breakdown the command:

1. `docker` - this lets your machine know you are using docker
2. `run` - this runs a container from the docker file in the directory.
3. `-d` - this tells docker to run the container in the background
4. `-p` - this will map the port from the host to the container
5. `-t` - Allocate a pseudo-tty
6. `hello` - This is the container name to run.

You can now access the container on port 8080.

`http://localhost:8080/hello`

To see containers running on your machine:

`docker ps`

(add -a to see all containers)

This will return something like: 

`CONTAINER ID   IMAGE     COMMAND    CREATED          STATUS          PORTS                    NAMES`

`aa80fad07fb2   hello     "/hello"   14 minutes ago   Up 14 minutes   0.0.0.0:8080->8080/tcp   goofy_roentgen`

We can now stop the container:

`docker stop hello`

Let clean up:

Reomve the the container:

`docker rm hello`

Remove the image:

`docker rmi hello`
