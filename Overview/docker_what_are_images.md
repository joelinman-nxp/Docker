# What are Container Images

Container images are like snapshots of an application and its dependencies at a particular point in time. They are read-only templates that can be used to create containers, and they can be shared and re-used across different environments and systems.

For example, a container image for a LAMP (Linux, Apache, MySQL, PHP) stack might include the Linux operating system, the Apache web server, the MySQL database server, and the PHP runtime and libraries, along with any other dependencies required by the application.

## Using Images in Containers

To use an image to create a container, you would typically define a YAML file that specifies the configuration and settings for the container. Here's an example of a simple YAML file for a LAMP stack container:

```yaml
version: '3'
services:
  web:
    image: my-lamp-stack:latest
    ports:
      - "80:80"
    volumes:
      - ./app:/var/www/html
    environment:
      MYSQL_ROOT_PASSWORD: my-secret-pw
      MYSQL_DATABASE: my-db
      MYSQL_USER: my-user
      MYSQL_PASSWORD: my-pw
    depends_on:
      - db
  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: my-secret-pw
      MYSQL_DATABASE: my-db
      MYSQL_USER: my-user
      MYSQL_PASSWORD: my-pw
    volumes:
      - ./db:/var/lib/mysql

```
## What is being defined in the Stack above?

In this example, the YAML file defines two services: `web` and `db`. The `web` service is based on the `my-lamp-stack` image, which includes the Apache web server, the PHP runtime, and the application code. The `db` service is based on the `mysql:5.7` image, which includes the MySQL database server.

The `web` service is configured to expose port 80 and to mount a volume that maps the `./app` directory on the host machine to the `/var/www/html` directory in the container. It also sets some environment variables that configure the MySQL database connection.

The `db` service is configured to set some environment variables that configure the MySQL root password, database name, user, and password. It also mounts a volume that maps the `./db` directory on the host machine to the `/var/lib/mysql` directory in the container.

## Running the Stack

If you were to run this YAML file with Docker Compose, it would create two containers: one for the web service and one for the `db` service. The `web` container would use the `my-lamp-stack` image to run the application code and serve it through the Apache web server, while the `db` container would use the `mysql:5.7` image to provide the database server.

## Images: Best Practices

When creating images, it is important to follow these best practices to help ensure your images are secure, efficient, and easy to maintain.

- **Keep images small** - To reduce the size of images, use a minimal base image, remove unnecessary files and packages, and use multi-stage builds to avoid including build artifacts in the final image.

- **Use a minimal and secure base image** - Use a base image that is regularly updated and has a small attack surface, such as Alpine Linux or Debian.

- **Avoid running as root** - Avoid running containers as root to minimize the impact of security vulnerabilities. Use a non-root user instead.

- **Use environment variables for configuration** - Use environment variables to pass configuration options to containers, rather than hardcoding them in the image. This allows for more flexibility and easier maintenance.

- **Use a single process per container** - Use a single process per container to simplify management and improve security. Use container orchestration tools like Kubernetes or Docker Compose to manage multiple containers.

- **Avoid storing sensitive information in images** - Avoid storing secrets, passwords, or other sensitive information in container images. Instead, use environment variables or external secrets management systems like Hashicorp Vault or AWS Secrets Manager.

- **Label images for easy identification** - Use labels to provide metadata about images, such as version, maintainer, or dependencies. This can make it easier to identify and manage images in a repository.

Overall, following these best practices can help create container images that are secure, efficient, and easy to maintain, while minimizing the risk of vulnerabilities and increasing portability and scalability.
