# Understanding Docker: A Modern Containerization Platform
---
 Docker is more than just a buzzword—it's a game-changer for modern infrastructure. It allows you to package applications and their dependencies into lightweight, portable containers that run consistently across environments—from your laptop to production.
---
## What is Docker?

Docker is an open-source containerization platform that allows
developers and IT professionals to build, ship, and run applications
inside lightweight, portable containers.

In simple terms, Docker packages an application along with all its
dependencies---such as libraries, frameworks, and configuration
files---into a single unit called a container. This ensures that the
application runs consistently across different environments, from a
developer's laptop to production servers.

---
# Docker vs Virtual Machines (VMs)

## Docker Containers
Docker is a containerization platform that packages applications and their dependencies into isolated units called containers. These containers share the host operating system's kernel, making them lightweight and fast.

### Key Features:
•	Lightweight: No need for a full OS per app.\
•	Fast Startup: Containers launch in seconds.\
•	Portability: Runs consistently across environments.\
•	Efficiency: Uses fewer system resources.\
•	Ideal For: Microservices, CI/CD pipelines, cloud-native apps.


## Virtual Machines (VMs)
VMs emulate entire operating systems using a hypervisor. Each VM includes its own guest OS, libraries, and application stack, running on top of the host OS.

### Key Features:
•	Full Isolation: Each VM is fully independent.\
•	Slower Startup: Boot times are longer due to OS overhead.\
•	Resource Intensive: Requires more CPU, RAM, and storage.\
•	Flexibility: Can run different OS types on the same host.\
•	Ideal For: Legacy applications, multi-OS environments, full system emulation.

### Prerequisites

Before installation, consider the following:

- Firewall Compatibility: When you expose container ports using Docker,
these ports may bypass firewall rules configured with ufw or firewalld.##
- iptables Requirements: Docker supports iptables-nft and
iptables-legacy. Ensure your firewall rules use iptables or ip6tables,
and add them to the DOCKER-USER chain.

### Supported Ubuntu Versions (64-bit)

• Ubuntu Questing 25.10\
• Ubuntu Plucky 25.04\
• Ubuntu Noble 24.04 (LTS)\
• Ubuntu Jammy 22.04 (LTS)\
\
Supported Architectures: x86_64 (amd64), armhf, arm64, s390x, ppc64le

### Install using the convenience script

```bash
sudo apt-get update
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh --dry-run
docker --version
docker run hello-world

```

When you run docker run it will download an image file and run a container.
---
### So what is image and container in docker?
### Docker Image: 
A Docker image is a read-only blueprint for a container. It contains everything needed to run an application.

### Docker Container: 
A Docker container is a running instance of a Docker image. It’s a lightweight, isolated environment where your application executes.

--- 
If we run the

```bash
docker run nginx
```
It will run the container and lock the terminal. If we exit from the terminal it will be stop. 


 To solve the issue we need to run the image in detach mode. The command will be

 ```bash
docker run -d  nginx
```

In this command the container will run in detach mode. 


But if the server is down or reboot the container will not run automatically. We need to run the container again manually. In production there will be run many containers, manually run containers will be difficult. To resolve the issue we can run this command.

 ```bash
docker run -d  --name=nginx-1 --restart=always nginx
```

Now our nginx is running, but it will be reachable because of port issue. We need to port mapping with our server port and container port. To fix the issue we need to run the below command. 

 ```bash
docker run -d  --name=nginx-1 -p 80:80 --restart=always nginx
```

To make a container in image for shiping we can use below command


 ```bash
docker save nginx:v1 | gzip > nginx.tar.gz
```
For import this image to other docker engine we can use below command 
 ```bash
docker load -i nginx.tar.gz
```
