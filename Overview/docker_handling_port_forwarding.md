# How to handle Port Forwarding in Docker

## What is port forwarding in Docker?

Port forwarding is a way to expose a container's network ports to the host machine or to other containers. By default, a container's network is isolated from the host machine and other containers, but port forwarding allows you to map a container's port to a port on the host machine or to a different container.

## Why use Docker port forwarding?

Docker port forwarding is essential for many containerized applications, as it allows them to be accessed from outside the container. Without port forwarding, applications running inside a container would only be accessible from within the container itself, which is obviously not very useful for **most** applications.

---

## Types of Docker port forwarding

### There are two types of port forwarding in Docker:
---

- **Host port forwarding** - With host port forwarding, a port on the host machine is mapped to a port in the container. This allows traffic to be sent to the container through the mapped port on the host machine.

- **Container port forwarding** - With container port forwarding, a port in the container is mapped to a different port in the same container or a different container. This is useful when multiple containers need to communicate with each other.

## How to use Docker port forwarding

To use port forwarding in Docker, you need to specify the ports to be forwarded when running a container. This can be done using the -p or --publish flag, followed by the port numbers to be forwarded.

For example, to map port 80 on the host machine to port 8080 in a container, you can use the following command:

`docker run -p 80:8080 my_image`

In this example, the -p 80:8080 flag maps port 80 on the host machine to port 8080 in the container.

You can also specify multiple port mappings by using the -p flag multiple times, like this:

`docker run -p 80:8080 -p 443:8443 my_image`

In this example, port 80 on the host machine is mapped to port 8080 in the container, and port 443 on the host machine is mapped to port 8443 in the container.

you can also define the protocol too:

`docker run -p 80:8080/tcp -p 80:8080/udp my_image`

In this final example, port 80 on the host machine is mapped to port 8080 in the container for both TCP and UDP protocols.

### Docker Compose Port Mapping Example

```yaml
services:
  myservice:
    image: myimage
    ports:
      - "80:8080" 
# maps port 80 on the host machine to port 8080 in the container 
```

## Managing Docker port mappings

You can view the port mappings of a running container using the `docker port` command. For example, to view the port mappings of a container named mycontainer, you can use the following command: 

`docker port my_container`

You can also remove a port mapping by stopping and removing the container, or by using the `docker container rm` command with the `--rm` flag.

---

Docker port forwarding is a crucial feature for containerized applications that need to be accessed from outside the container. By mapping ports on the host machine to ports in a container, traffic can be routed to the container, allowing applications to be accessed from the host machine or other machines on the network.