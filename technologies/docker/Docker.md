# Docker Overview

Docker allows you to develop software without having to make changes to your local system.

## How It Works

1. **Docker File**: You start off with a Docker file, which is a blueprint that tells Docker how to configure the environment that runs the application. The Docker file works in layers. [Example Dockerfile](Dockerfile)

2. **Images**: Images are templates for running the application. Images capture code and your environment, similar to how GitHub captures your code. However, GitHub does not run your code; you need GitHub Pages to run your code or you have to manually run it. Images don't do much besides capturing code—that's where containers come in.

3. **Containers**: A container will run your image. Containers are standardized and have everything the application needs to run.

## Benefits

The benefits of Docker include:

- You can easily run different versions of applications without conflicts.
- It provides a standardized way of running applications where there are no conflicts with the operating system.

## Technologies I have used with Go

[GoLang](technologies/GoLang.md)
- Containerized Go application.

