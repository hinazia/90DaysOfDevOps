## Task 1: The Problem

 1. Write what happened and why?
    - When the container is removed/deleted, all the data in it is also removed along with it.
    - When the new container of the same image will be created, it will have fresh and new storage without the previous container's data. 


## Task 3: Bind Mounts

 1. Write in your notes: What is the difference between a named volume and a bind mount?
    - a named volume is a storage managed by dockerand is used to persist data even when the container is deleted. Data can be reused by another container.
    - in bind mount, a specific folder is mounted to the container and changes made to files and folders are reflected in real time between host and container

## Task 4: Docker Networking Basics

 1. Run two containers on the default bridge — can they ping each other by name?
    - No they cannot. On default bridge, they ping through  their IP Address
      docker exec [CONTAINER ID] ping [OTHER CONTAINER IP]
    - Build a custom bridge to ping by names as IP adresses of the containers can change
      

## Task 5: Custom Networks

 1. Write in your notes: Why does custom networking allow name-based communication but the default bridge doesn't?
    - Containers can communicate using their IP addresses, but Docker's built-in DNS does not automatically provide name-based resolution between containers.
    - A custom bridge network comes with Docker's built-in DNS service.
