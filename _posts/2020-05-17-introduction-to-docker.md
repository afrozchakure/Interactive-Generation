---
date: 2020-05-17 12:20:00
title: Introduction to Docker
subtitle: Learn the why, what and how of Docker
description: Introduction to Docker
image: https://cdn-images-1.medium.com/max/716/0*XaGgN0G--22Lk26h.png
optimized_image: https://cdn-images-1.medium.com/max/716/0*XaGgN0G--22Lk26h.png
category: machine-learning
tags:
  - technology
  - machinelearning
  - datascience 
  - deeplearning 
  - algorithms
layout: single
comments: true
author_profile: true
toc: true
---

<figure>
<center><img src="https://miro.medium.com/max/400/1*dKiymnX_yJnWc6Xs5-oMfg.jpeg" alt = "Docker">
<figcaption>Docker</figcaption>
</center>
</figure>

In this blog we’ll try to understand one of the most popular tools used to **containerize and deploy applications** over the internet i.e. Docker. It makes deploying applications extremely simple.

We will try to look at the things that make Docker so special and learn how you can **build, deploy, and fetch applications** using Docker & Docker Hub using just a few steps.

## What is Docker ?
1. It is a tool used to **create, deploy and run applications by using containers.**
2. Containers allows developers to **package up an application with all the parts it needs.**
3. Containers are **isolated from one another and bundle their own software, libraries and configuration file.**

## Difference between Docker Containers and Virtual Machines
### 1. Docker Containers
- Docker Containers contain **binaries, libraries and configuration files along with the application itself.**
- They don’t contain a guest OS for each container and rely on the underlying OS kernel, which makes the containers **lightweight.**
- Containers **share resources with other containers** in the same host OS and **provide OS level process isolation.**

### 2. Virtual Machines
- Virtual Machines (VMs) run on **Hypervisors**, which **allow multiple Virtual Machines to run on a single Machine** along with its own operating system.
- Each VM has its own copy of an operating system along with the application and necessary binaries, which makes it significantly **larger and it requires more resources.**
- They provide **Hardware-level process isolation** and **are slow to boot.**

<figure>
<center><img src="https://miro.medium.com/max/700/1*m3Q6wcXPrmKLn1xhvf7F8g.png" alt = "Docker vs Virtual Machines">
<figcaption>Docker vs Virtual Machines</figcaption>
</center>
</figure>

## Important Terminologies in Docker:
### 1. Docker Image
- It is a file, comprised of multiple layers, used to execute code in a Docker container.
- They are a set of instructions used to create docker containers.

### 2. Docker Container
- It is a runtime instance of an image.
- Allows developers to package application with all parts needed such as libraries and other dependencies.

### 3. Docker file
-It is a text document that contains necessary commands which on execution helps assemble a Docker Image.
- Docker image is created using a Docker file.

### 4. Docker Engine
- The software that hosts the containers is named Docker Engine.
- Docker Engine is a client-server based application

It consists of 3 main components :
1. **Server**: It is __responsible for creating and managing Docker images, containers, networks and volumes__ on the Docker. It is referred to as a **daemon process**.
2. **REST API**: It specifies how the applications can interact with the Server, and instructs it what to do.
3. **Client**: The Client is a docker command-line interface (CLI), that allows us to interact with Docker using the docker commands.

<figure>
<center><img src="https://miro.medium.com/max/492/1*MYX0ClbWoitxS0RNUVvj8A.png" alt = "Components of Docker Engine (Credits: Docker.com)">
<figcaption>Components of Docker Engine (Credits: Docker.com)</figcaption>
</center>
</figure>

### 5. Docker Hub
- Docker Hub is the **official online repository** where you can find other Docker Images that are available for use.
- It makes it easy to **find, manage and share container images** with others.

## Installing Docker on Ubuntu
### 1. Remove old version of Docker

```shell
$ sudo apt-get remove docker docker-engine docker.io containerd runc
```

### 2. Installing Docker Engine

```shell
$ sudo apt-get update
$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
$ sudo apt-key fingerprint 0EBFCD88
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable nightly test"
$ sudo apt-get update
$ sudo apt-get install docker-ce docker-ce-cli containerd.io// Check if docker is successfully installed in your system
$ sudo docker run hello-world
```

## Create an application in Docker
### 1. Create a folder with 2 files (Dockerfile and main.py file) in it.

```shell
. 
├── Dockerfile 
└── main.py 0 directories, 2 files
```

### 2. Edit main.py with the below code.

```python
#!/usr/bin/env python3
print(“Docker is magic!”)
```

### 3. Edit Dockerfile with the below commands.

```dockerfile
FROM python:latest
COPY main.py /
CMD [ “python”, “./main.py” ]
```

### 4. Create the Docker image.

Once you have created and edited the __main.py__ file and the __Dockerfile__, **create your image to contain your application.**

```shell
$ docker build -t python-test . The ’-t’ option allows to define the name of your image. ’python-test’ is the name we have choosen for the image.
```

### 5. Run the Docker image

Once the image is created, your code is ready to launch.

```shell
$ docker run python-test
```

## Push an Image to Docker Hub
### 1. Create an Account on [Docker Hub](https://hub.docker.com/).

<figure>
<center><img src="https://miro.medium.com/max/700/1*rSwQoZ04pmEhh1GBK27x0g.png" alt = "Create Account on Docker Hub">
<figcaption>Create Account on Docker Hub</figcaption>
</center>
</figure>

### 2. Click on “Create Repository” button, put the name of file and click on “Create”.

<figure>
<center><img src="https://miro.medium.com/max/700/1*gweBKbpz5gn3fdXnZb7eNA.png" alt = "Create Account on Docker Hub">
<figcaption>Create Account on Docker Hub</figcaption>
</center>
</figure>

### 3. Now will “tag our image” and “push it to the Docker Hub repository” which we just created.

```shell
# Run this commend to list docker images 
$ docker images
```

The above will give us this result

```shell
REPOSITORY                TAG      IMAGE ID     CREATED      SIZE 
afrozchakure/python-test  latest c7857f97ebbd   2 hours ago 933MB
```

Image ID is used to tag the image. The syntax to tag the image is:

```shell
docker tag <image-id> <your dockerhub username>/python-test:latest
```

```shell
$ docker tag c7857f97ebbd afrozchakure/python-test:latest 
```

### 4. Push image to Docker Hub repository

```shell
$ docker push afrozchakure/python-test
```

## Fetch and run the image from Docker Hub
1. To remove all versions of a particular image from our local system, we use the **Image ID** for it.

```shell
$ docker rmi -f af939ee31fdc 
```

2. Now run the image, it will fetches the image from docker hub if it doesn’t exist on your local machine.

```shell
$ docker run afrozchakure/python-test
```

## Conclusion:

So you have learnt about the basics of Docker, the difference between Virtual Machines and Docker Containers along with some common Terminologies in Docker.

Also we went through the installation of Docker on our systems. We created an application using Docker and pushed our image to Docker Hub.

Lastly we learned how we could remove a particular image from our local system and later pull the image from Docker Hub if it doesn’t exist locally.