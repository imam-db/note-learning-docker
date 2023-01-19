## Notes my learning about docker


### What is docker?

Docker is like a big box that can hold many smaller boxes inside. Each smaller box is called a "container" and it has everything it needs to run a program or play a game, like the instructions, tools and toys. And the big box called "Docker" can take care of the smaller boxes, make sure they have what they need and help them talk to each other if they need to play together. This way, we can run many programs and games at the same time without them getting in each other's way. And we can also easily move the smaller boxes from one big box to another, and it will work the same way.


### Containers vs Images

In Docker, an image is a lightweight, stand-alone, executable package that includes everything needed to run a piece of software, including the code, a runtime, libraries, environment variables, and config files. An image is created by using a set of instructions called a Dockerfile.

A container is a running instance of an image. When you start a container, Docker takes the image and adds a read-write layer on top. This allows you to make changes to the container, such as writing new files or modifying existing files. However, changes made to a container do not affect the underlying image.

In short, an image is a blueprint for a container, and a container is a running instance of that blueprint. You can create multiple containers from the same image, and each container will have its own unique set of changes on top of the underlying image.


### Docker commands

Some common commands:
- `docker run`  : used to run a container from a specified image
- `docker start`: used to start a stopped container
- `docker stop` : used to stop a running container
- `docker ps`   : used to display a list of running containers
- `docker pull` : used to pull an image from a registry
- `docker push` : used to push an image to a registry
- `docker build`: used to build an image from a Dockerfile
- `docker exec` : used to execute a command inside a running container
- `docker logs` : used to display the logs of a container
- `docker rm`   : used to remove a stopped container


#### docker run

`docker run` is a command used to start a new container from an image. The basic syntax of the command is:

```docker
docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
```

- `IMAGE` is the name of the image that you want to run.
- `COMMAND` is the command that you want to run inside the container.
- `ARG...` are any additional arguments that you want to pass to the command.

The docker run command has a lot of options that you can use to configure the container, such as:

- `-d` or `--detach` : runs the container in detached mode, which means it runs in the background and doesn't attach to the current terminal.
- `-p` or `--publish` : maps a host port to a container port, so you can access the container's services from the host.
- `-v` or `--volume` : mounts a host directory or a named volume as a container directory.
- `-e` or `--env` : sets environment variables in the container.
- `-it` : it allows you to interact with the container via the command line and it also allows you to have a terminal-like experience inside the container.


#### docker run example

```docker
docker run -d --name myredis redis
```

This command will start a new container from the `redis` image, give it the name `myredis`, and run it in `detached` mode. The container will continue running in the background and you will be able to run other commands in the terminal.

```docker
docker run --name mydb -d mysql
```

This command will start a new container from the `mysql` image, give it the name `mydb`, and run it in `detached` mode. Now you can refer to this container by its name `mydb` instead of its container ID when you want to stop, start or inspect it.

```docker
docker run -p 8080:80 --name mynginx -d nginx
```

The `-p` or `--publish` option is used to map a host port to a container port. The format is `host-port:container-port`. In this command, the `8080:80` is used to map port 8080 of the host to port 80 of the container. Therefore, the host port is in front: 8080, and the container port is in back: 80. It means that when you access port 80 of the host, the traffic will be forwarded to port 80 of the container, where the nginx server is running.


```docker
docker run -it --name myubuntu ubuntu bash
```

This command will start a new container from the `ubuntu` image, give it the name `myubuntu`, attach a pseudo-TTY to the container and run the command `bash` in interactive mode. Now you can run commands inside the container and see the results.

```docker
docker run -it --name mypython python
```

This command will start a new container from the `python` image, give it the name `mypython`, and attach a pseudo-TTY to the container. You will be able to run Python commands and scripts inside the container by starting the python interpreter by running `python` command.