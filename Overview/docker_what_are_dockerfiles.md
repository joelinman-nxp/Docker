# What are Dockerfiles

Dockerfiles are a set of instructions that specify how to build a Docker image. A Docker image as i have learned, is a lightweight, standalone, executable package that includes everything needed to run an application, including code, libraries, and dependencies.

## What makes up a Dockerfile

## how to make a Dockerfile

- **Choose a base image** - Start by selecting a base image that provides the minimum set of features needed to run your application. For example, you could use a base image that includes a particular version of the operating system and programming language.

- **Define dependencies** - Use the Dockerfile to specify the dependencies required to run your application. This could include libraries, frameworks, or other software packages.

- **Copy application files** - Use the Dockerfile to copy the files needed to run your application into the image. This could include source code, configuration files, and any other necessary files.

- **Set environment variables** - Use the Dockerfile to set any environment variables needed to run your application. For example, you might set a PORT variable to specify the port number that your application listens on.

Using environment variables is important ot protect sensitive 

- **Define the default command** - Use the Dockerfile to specify the default command that should be run when the image is launched. This command should start your application.