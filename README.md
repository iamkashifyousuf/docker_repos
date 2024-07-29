Setting Up a Local Docker Registry
==================================

This setup allows you to create a private repository where you can store, manage, and distribute Docker images within your development environment. By configuring a local Docker registry, you gain a dedicated space to host your custom Docker images, facilitating efficient development, testing, and deployment workflows. The configuration ensures that the registry is accessible on a specified port and persists data in a designated directory, making it a reliable and convenient solution for handling Docker images locally.

The provided docker-compose.yml file defines a Docker Compose setup using version 3, configuring a service named registry that uses the official registry:2 image to run a Docker registry. This service maps port 5000 inside the container to port 5001 on the host machine, allowing external access through localhost:5001. The registry's storage is directed to the /data directory inside the container, with a volume mapping that binds this directory to ./data on the host machine, ensuring data persistence. This setup facilitates the creation and management of a local Docker registry, ideal for storing and distributing Docker images within a development environment.

Cloning the Repository
----------------------
First, clone the repository containing the docker-compose.yml file.
```shell
git clone https://github.com/iamkashifyousuf/docker_repos.git
cd docker_repos
```
Starting the Local Registry
---------------------------
Bring up the Docker registry service using Docker Compose.
```shell
docker-compose up -d
```
Tagging an Image for the Local Registry
---------------------------------------
To push an image to your local registry, you need to tag it first. Here, we'll use the busybox image as an example:
```shell
docker pull busybox
docker tag busybox localhost:5001/my-busybox:latest
   ```
This tags the busybox image for the local registry at localhost:5001 with the repository name my-busybox and tag latest.

Pushing the Image to the Local Registr
--------------------------------------
Push the tagged image to the local registry:
```
docker push localhost:5001/my-busybox:latest
```
Pulling the Image from the Local Registry
-----------------------------------------
To pull the image back from your local registry, use the following command:
```shell
docker pull localhost:5001/my-busybox:latest
```
Verifying the Image
-------------------
```shell
docker images
```
Look for localhost:5001/my-busybox in the repository list to confirm the image is available locally.
By following these steps, you can efficiently push and pull Docker images to and from your local registry, enhancing your development and testing workflows
