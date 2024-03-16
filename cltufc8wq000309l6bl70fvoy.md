---
title: "Day 30: Containerization (Docker) with Python"
seoTitle: "Containerization (Docker) with Python"
seoDescription: "This is the thirtieth blog post in my Python learning journey. "
datePublished: Sat Mar 16 2024 18:31:24 GMT+0000 (Coordinated Universal Time)
cuid: cltufc8wq000309l6bl70fvoy
slug: day-30-containerization-docker-with-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1710608008962/db1f8c99-1f48-40ea-8abb-1b843e3c4f87.png
tags: image-processing, docker, python, devops, containers, fastapi

---

This is the thirtieth blog post in my Python learning journey. In this post, we will delve into Containerization, exploring its significance and the reasons why it's essential. Additionally, we'll embark on a project creation journey and containerize the project to demonstrate the practical implementation of containerization.

### Docker

Docker is a platform and toolchain that allows developers to build, package, distribute, and run applications and services in lightweight, isolated environments called containers.

term in docker:

* **Container:** Docker uses containerization technology to create containers, which are lightweight and portable environments that include everything needed to run an application or service (code, runtime, system tools, libraries, and settings). Containers are isolated from each other and share the host operating system's kernel, making them efficient and resource-friendly.
    
* Image: Docker uses images as the basis for containers. An image is a read-only template that contains instructions for creating a container. It includes the application or service code, dependencies, and runtime environment. Images are created using a Dockerfile, which specifies the steps to build the image.
    
* **Dockerfile:** Dockerfile is used to create an Image of our application. we can write all configurations on this file. Dockerfiles allow developers to automate the image creation process and ensure consistency across environments.
    

### Containerize fast API application

```dockerfile
# Python base image
FROM python:3.9

# Set the working directory
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY requirements.txt .

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Copy the current directory contents into the container at /app
COPY . .

# Make port 3000 available to the world outside this container
EXPOSE 3000

# Run app.py when the container launches
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "3000"]
```

This is a Dockerfile to create an image for our Python application. To run this file command is mentioned below.

```powershell
docker build -f file-path -t image-name .
```

After running this file image will be created.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710613705470/cc4da3dc-8aff-4ca8-89c2-8f1897abca23.png align="center")

### Conclusion

Docker is a platform for building, packaging, distributing, and running applications in isolated containers. Containers are lightweight and self-sufficient environments that contain all the necessary dependencies to run an application. Docker uses images as templates for creating containers, and Dockerfiles specify the steps to build these images.

The provided Dockerfile demonstrates how to containerize a FastAPI application in Python, set up the environment, install dependencies, expose a port, and run the application with unicorn.

To summarize, Docker enables efficient and portable application deployment through containerization, improving consistency and scalability in software development and deployment processes.

Thankyou💕💕