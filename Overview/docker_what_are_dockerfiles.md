# What are Dockerfiles

Dockerfiles are a set of instructions that specify how to build a Docker image. A Docker image as i have learned, is a lightweight, standalone, executable package that includes everything needed to run an application, including code, libraries, and dependencies.

## What makes up a Dockerfile

below, i have listed some of the most common Dockerfile statements along with some parameter examples:

`FROM`: This statement specifies the base image that your image will be built on top of. The parameter is simply the name and tag of the base image. For example: `FROM ubuntu:latest`.

`RUN`: This statement runs a command inside the container. The parameter is a string or an array of strings, which represents the command to run. For example: `RUN apt-get update && apt-get install -y curl`.

`COPY`: This statement copies files from the host machine to the container. The first parameter is the path to the files on the host machine, and the second parameter is the path where the files will be copied to in the container. For example: `COPY . /app`.

`WORKDIR`: This statement sets the working directory for any subsequent commands in the Dockerfile. The parameter is simply the path to the working directory. For example: `WORKDIR /app.`

`CMD`: This statement sets the default command to run when the container starts. The parameter is a string or an array of strings, which represents the command to run. For example: `CMD ["node", "app.js"]`.

`EXPOSE`: This statement exposes a port from the container to the host machine. The parameter is simply the number of the port to expose. For example: `EXPOSE 80`.

`ENV`: This statement sets an environment variable inside the container. The parameter is a key-value pair, where the key is the name of the environment variable and the value is its value. For example: `ENV MY_VAR=my_value`.

---

### Further/Advanced Statements to consider

`MAINTAINER`: This statement is used to identify the author or maintainer of the Dockerfile. The parameter is simply the name and email of the maintainer. For example: `MAINTAINER Joel Inman <joelinman@example.com>`.

`LABEL`: This statement adds metadata to the Docker image. The parameter is a key-value pair, where the key is the name of the label and the value is its value. For example: `LABEL version="1.0" description="My cool web app"`.

`ADD`: This statement is similar to the COPY statement, but it also supports downloading files from URLs and unpacking archives. The first parameter is the source file or URL, and the second parameter is the destination path in the container. For example: `ADD https://github.com/myuser/myapp/archive/master.tar.gz /app`.

`USER`: This statement sets the user that any subsequent commands will be run as. The parameter is simply the username or UID of the user. For example: `USER myuser`, **IMPORTANT** as you do not want to be running your containers as root for obvious security reasons.

`VOLUME`: This statement creates a mount point for a volume from the host machine or another container. The parameter is simply the path where the volume will be mounted in the container. For example: `VOLUME /var/log`.

`ARG`: This statement defines a build-time variable that can be passed in using the `--build-arg` flag when building the Docker image. The parameter is the name of the variable and an optional default value. For example: `ARG NODE_ENV=production`.

`ENTRYPOINT`: This statement sets the default command to run when the container starts, but also allows additional arguments to be passed in when starting the container. The parameter is a string or an array of strings, which represents the command to run. For example: `ENTRYPOINT ["npm", "start"]`.

---

## how to make a Dockerfile

- **Choose a base image** - Start by selecting a base image that provides the minimum set of features needed to run your application. For example, you could use a base image that includes a particular version of the operating system and programming language.

- **Define dependencies** - Use the Dockerfile to specify the dependencies required to run your application. This could include libraries, frameworks, or other software packages.

- **Copy application files** - Use the Dockerfile to copy the files needed to run your application into the image. This could include source code, configuration files, and any other necessary files.

- **Set environment variables** - Use the Dockerfile to set any environment variables needed to run your application. For example, you might set a PORT variable to specify the port number that your application listens on.

Using environment variables is important ot protect sensitive 

- **Define the default command** - Use the Dockerfile to specify the default command that should be run when the image is launched. This command should start your application.