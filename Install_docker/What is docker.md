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
•	Ideal For: Microservices, CI/CD pipelines, cloud-native apps.\


## Virtual Machines (VMs)
VMs emulate entire operating systems using a hypervisor. Each VM includes its own guest OS, libraries, and application stack, running on top of the host OS.

### Key Features:
•	Full Isolation: Each VM is fully independent.\
•	Slower Startup: Boot times are longer due to OS overhead.\
•	Resource Intensive: Requires more CPU, RAM, and storage.\
•	Flexibility: Can run different OS types on the same host.\
•	Ideal For: Legacy applications, multi-OS environments, full system emulation.\

### Prerequisites

Before installation, consider the following:\

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