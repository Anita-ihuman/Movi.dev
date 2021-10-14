## The Beginners Intro to Containerized Platforms:  Docker

If you are in the IT field, you must have encountered "Docker" on various media platforms. I have heard this word so much; I decided to find out what the fuss is all about. 

This article will look at the history of how Containerized tools( Docker) came into existence, what Docker is, its core components, and finally, the benefits of Docker.  If you are new to DevOps, you might want to keep reading. 


## How Containerized tools got introduced
 Before the existence of Containerized tools(Docker), applications and software experienced the difficulty of compatibility. Whenever there was a switch in the Operating System(either because a new developer joined a team), there were no certainties of the project running on their Operating System(OS).
This was because they experienced so many complexities of installing the various web servers, databases, orchestration tools and libraries. 

Even with this, they had to make sure they installed a similar OS, same as everyone on the project, they established the correct version, using the proper commands, and all this was done single-handedly by the new developers before the project would finally run.
There are no guarantees that if you shipped the project to another Operating system, it would perform the same way. This made the process of developing, building, and shipping projects extremely complex, challenging and with a lot of security vulnerabilities.

### Containerization
This is the process of putting together an application's code and the dependencies, libraries, and configuration files that the application needs to launch and operate efficiently in an isolated environment. Although the concept of an isolating environment is not new, the one containerization tool that has grown in popularity and demand over the years is [Docker ](https://www.docker.com/) 
## What is Docker:
Docker is an Open source containerization tool used to build, run, and package applications for deployment in an isolated environment. Similar to a Virtual Machine, except it's faster and runs in the same environment.
 Docker helps with the compatibility and scalability challenges previous applications face; It allows you to run the components in a separate container on a virtual machine. This means that the developers are expected to build a Docker configuration. With a simple Docker command, you can run the project on your device irrespective of the Operating system used.

![images.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1630956750649/NFusWwk2U.jpeg)
 [img source](https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.zekelabs.com%2Fblog%2FWhy-Learning-Docker-Containers-is-so-important-in-IT%2F&psig=AOvVaw0eCXlSheL2bqTJNCIqlK3C&ust=1631042935289000&source=images&cd=vfe&ved=0CAwQjhxqFwoTCLidz_OK6_ICFQAAAAAdAAAAABAQ) 
### Virtual Machine
Virtual Machines (VM) are an abstraction of physical hardware, turning one server into many servers. With the help of a hypervisor, multiple VM's can run on a single machine. Each VM contains a copy of an OS, an application, dependencies, and libraries, which take up tons of high disc space. 

![Container-vs-VMs.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1630957329576/GPDUcJQQh.jpeg)
 [img source](https://techglimpse.com/docker-installation-tutorial-centos/) 
## Components of a Docker architecture 

### Containers: 
The container is an abstraction of the app layer that packages code and dependencies. These are isolated environments containing their processes, network and mounts, just like the Virtual Machine, except they share a similar OS kernel. You can have multiple containers running on the same machine, each container running as an isolated process. Containers have existed for over 10 years (eg.  [LXC/LXD](https://discuss.linuxcontainers.org/t/comparing-lxd-vs-lxc/24) ,  [LXCF](http://lxcf.osdn.jp/index.html.en) ...)

When I said they share a similar OS kernel, I mean in a system with an Ubuntu OS, for instance, that has Docker installed- Docker can run any other OS on it so long as it is based on the same kernel.
The Windows OS is the only exception among all other operating systems.
 It does not share a similar kernel as Ubuntu, fedora, mac, etc. So it requires Docker to be run on a separate windows server.
You can say that you have run Docker on a Windows OS before and run Linux containers. 

What happens is, you are not running Linux containers on Windows; instead, Windows is running a Linux virtual machine under the hood. So it is just Linux containers on a Linux virtual machine that you have on your Windows.
The purpose of Docker is to package applications and put them in a container to ship them anywhere at any time necessary quickly.


**Operating System:**

The Operating System(OS) is the program that lets you interact with your computer. The operating system is the essential software on your computer. The OS works together with the computer memory and processes and all of its software and hardware. There are several different operating systems; two of the most common are  [macOS ](https://www.apple.com/macos/big-sur/) (which runs on all new Macs) and  [Microsoft Windows](https://www.microsoft.com/en-us/windows) (which comes preloaded on most computers).

### Docker Image
This is a template for creating an environment of your choice. Either an app, database or anything at all. An image is special because it contains everything that your application needs to run (an OS, software application, code, libraries, dependencies etc.)


 **How the concept of Images came about:**

In a production cycle, developers create an application and hand it over to the operation team to deploy and manage it in the production environment, giving them instructions or information regarding how to set up the app host, prerequisite installation, and dependencies be configured. When setting this application up, the DevOps team will most likely encounter some challenges, so they work with the developers to resolve them.

In Docker, developers and the operations team work together to transform those instructions into a Docker file with the requirements. This Docker file is therefore used to create a Docker image for the application. The image can run on any host with Docker and is guaranteed to run the same way anywhere until finally deployed. Most organizations have their application containerized and available in a public Docker repository called [Docker Hub.](Link) 

### Registry 
The registry is a highly scalable server-side application that stores and lets you distribute Docker images. Images are found in a registry where developers, organizations and anyone can host their project for other developers to use(e.g.,  [hub.docker.com](https://hub.docker.com/),  [Quay.io](https://quay.io/)  &  [Amazon ECR](https://aws.amazon.com/ecr/).
)

** Types of registry**
- Private registry
- Public registry

### Docker Engine
Docker Engine can be considered an application installed on the system that manages containers, images, and builds. Docker Engine acts as a client-server application with:

1. 
The Docker Daemon is the server that runs on the host machine.

1. 
 [APIs](https://www.bmc.com/blogs/microservice-vs-api/)  that permit the client to talk to and instruct the Docker daemon.

1. 
A command-line interface (CLI) client for sending instructions to the Docker Daemon using the special  [Docker commands](https://docs.docker.com/engine/reference/commandline/cli/).

## Benefits of Docker
- Runs containers within seconds
- Fewer resources which result in less disc space consumption
- Consumes less memory
- Does not require a complete new OS for each container.
- Works in any environment
- Takes care of scalability and compatibility

## Container Orchestration: 
This is a solution that consists of a set of tools and scripts that help host containers in a production environment. It typically consists of multiple Docker hosts containers so that, even if one fails, it is still replaced and managed.

![Img1DocAndKub.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630957662560/MCcTAfB0w.png)
 [img source](https://geekflare.com/docker-vs-kubernetes/) 

**Examples of Orchestration solutions **

-  [Docker Swarm ](https://docs.docker.com/engine/swarm/) 
-  [Kubernetes](http://kubernetes.io/) 
- [ Mesos](http://mesos.apache.org/) 

## Relationship between Docker and Kubernetes
Docker and Kubernetes are very different technologies that are highly complementary, and together, they make a powerful combination. One cannot pick one over another and can be perfectly combined to create, deliver successfully, and scale containerized applications. Docker is responsible for developing and deploying your application containers smoothly. 

As the containerized application grows more extensive and more complex, it becomes difficult to scale numerous container instances and ensure smooth interaction between different containers to coordinate and schedule containers. That's where [Kubernetes ](http://kubernetes.io/) comes in and takes care of orchestrating docker containers. Kubernetes uses Docker host to host applications in the form of Docker containers. 


![DockerVsK8s.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630957881814/8rmvi0iKL.png)
 [img source](https://geekflare.com/docker-vs-kubernetes/) 

## Conclusion
Great job reading through this article; I bet this gives you a clearer picture of what Docker is all about. Docker has since grown in popularity; developers are leveraging it in building and distributing applications across platforms without duplicating computing resources and avoiding redundancy. In subsequent articles, I will be introducing Kubernetes and a few fun facts about it.

### References
- https://www.bmc.com/blogs/docker-101-introduction/
- https://www.educative.io/blog/beginners-guide-to-docker
- https://docs.docker.com/engine/
- https://edu.gcfglobal.org/en/computerbasics/understanding-operating-systems/1/
- https://k21academy.com/docker-kubernetes/docker-vs-virtual-machine/