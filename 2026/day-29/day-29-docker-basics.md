### Task 1: What is Docker?

#### Research and write short notes on:

1. What is a container and why do we need them?
   
A lightweight package containing an application and all its dependencies.  
We need them in oder to run our apps on any platform, any OS and solves the ""It runs on my machine problem"

2. Containers vs Virtual Machines — what's the real difference?
   
  Virtual Machines : need "Allocated" resources exmaple Ram, Storage, OS installation etc
  Containers :       use "Shared" resources and saves up cost, storage, duplication of OS etc. is lightweight

3. What is the Docker architecture? (daemon, client, images, containers, registry)
   
  daemon : The Docker Engine running in the background. It builds images, creates containers, and manages Docker resources.
  client : Talks to the Docker Engine
  images : Blueprints (files) to create containers
  containers : A box where all our code is to run applications. A running instance of an image.
  registry : A repository for storing and sharing Docker images.
