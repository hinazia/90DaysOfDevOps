## Documentation

### Create day-45-docker-cicd.md with:

#### Your complete workflow YAML
```
name: Publish Docker File

on: workflow_dispatch
        
jobs:
    build:
        runs-on: self-hosted
        steps:
            - name: Checkout the code
              uses: actions/checkout@v6

            - name: Log In to Docker Hub
              uses: docker/login-action@v4
              with:
                username: ${{ vars.DOCKER_USERNAME }}
                password: ${{ secrets.DOCKER_TOKEN }} 

            - name: Set up QEMU
              uses: docker/setup-qemu-action@v4

            - name: Set up Docker Buildx
              uses: docker/setup-buildx-action@v4
              with:
                driver: docker-container

            - name: Build and push Docker Image on Main Branch Only
              
              uses: docker/build-push-action@v7
              with:
                context: .
                push: ${{ github.ref == '/refs/heads/main' }}
                tags: |
                    ${{ vars.DOCKER_USERNAME }}/repo:latest
                    ${{ vars.DOCKER_USERNAME }}/repo:${{ github.sha }}

```
#### Docker Hub link to your image
https://hub.docker.com/repository/docker/hinaqazi612/repo/general

#### Screenshot of the pipeline run
<img width="1422" height="292" alt="image" src="https://github.com/user-attachments/assets/9e8a06bd-a78b-4ca9-a328-4fb599677e7a" />

