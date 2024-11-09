Docker Project

This project demonstrates how to create a Dockerized web application using Nginx as the base image. The steps below will guide you through cloning the project, building and running the container, and pushing the image to Docker Hub.


Project Overview

The repository contains a sample website that will be served using an Nginx server running inside a Docker container. You will build the Docker image, run a container from it, and later push the image to your Docker Hub account for public or private access.
Steps

    Clone the Repository

    Download or clone the project from GitHub to your local machine:
        $ git clone https://github.com/Devops-Omar/Docker-Project.git

    Verify the Directory Structure

    Ensure that the Docker-Project directory and the required files exist:
        $ ls Docker-Project/sample-website/sample-website

    Create a Dockerfile

    Navigate to your project directory and create a Dockerfile using your preferred:
        $ vim Dockerfile

    Add the following content to the Dockerfile:
        FROM nginx:latest
        COPY ./Docker-Project/sample-website /usr/share/nginx/html/
        EXPOSE 8080

    Build the Docker Image

    Build the image from the Dockerfile using the command below:
        $ docker build -t webseite .

    Verify the Image Creation

    List your Docker images to ensure the new image has been created:
        $ docker images

    Run the Container

    Run a new container from the image and map port 8080 on your host to port 80 in the container:
        $ docker run -it --rm -d -p 8080:80 --name web webseite

    Access the Container in a Browser
        Open your web browser and go to http://localhost:8080 to see the sample website.

    Commit Changes to Create a New Image

    If you have made changes within the running container and want to save those changes as a new image, use the docker commit command:
        $ docker commit <container_id> [username_account]/[new_image_name]

    Example:
        $ docker commit q65ewdhcdc omarmembership/test-docker:v1

    Log in to Docker Hub

    **Log in to your Docker Hub account to push your image **
        $ docker login

    Push your new image to your Docker Hub repository:
        $ docker push omarmembership/docker-project

    Pull and Run the Image from Docker Hub
        $ docker pull omarmembership/docker-project
        $ docker run -it --rm -d -p 4000:80 --name webseite omarmembership/docker-project
