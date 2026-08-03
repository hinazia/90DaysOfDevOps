## IMPORTANT POINTERS

  I debugged a lot of real-world issues:

  - Docker build context
  - container filesystem
  - Express static serving
  - working directory problems
  - service-to-service networking
  - environment variables
  - Docker volumes
  - model persistence

  - In dockercompose file, always use build context meaning in custom images from Dockerfile
    always use `build: .` instead of `image:<image_name>` because whenever you will add new
    piece of code, it will not COPY automatically.
    
  -  Always do docker exec and go inside the container and do ls and all these linux commands to debug
  -  Never use randomly docker compose down -v, especially when working with Data persistance and Volumes. use withpot flag -v. it is safer
  -  Ollama model was wiped out beacuse it was pulled and saved in volume and with -v flag, it got wiped out

Here is a copy-paste friendly cheat sheet from this debugging session:

# Docker Debugging Cheat Sheet

### 1. Check running containers

See all running containers:

```bash
docker ps
````

### See Compose services:

docker compose ps

#### Check if multiple containers of the same service exist:

docker ps -a

#### Container Filesystem Debugging

Enter a running container
docker compose exec <service_name> sh

Example:
docker compose exec webapp sh

or:

docker exec -it <container_id> sh

#### Check current working directory inside container
pwd

### Important for problems where your app runs from the wrong folder.

List files inside container
ls

Detailed:

ls -la
Check if a file/folder exists
ls <path>

Examples:

ls /app
ls /app/public
ls /app/public/index.html
Find files inside container
find /app -name "index.html"

Example:

find /app -name "*.html"
Read file contents inside container
cat <file>

Example:

cat public/index.html
Docker Build Context Debugging
Rebuild image without cache

### Use when Docker is not copying latest files:

docker compose build --no-cache

#### For a specific service:

docker compose build --no-cache webapp

#### Check build output

Look for:

COPY .

Confirm Docker is copying your expected files.

Check Docker image exists
docker images

Check what is inside an image
Create temporary container:

docker run --rm -it <image_name> sh

Then:
ls
Docker Ignore Problems

Check if .dockerignore exists:

ls -la

#### View contents:

cat .dockerignore

Common issue:

public
frontend
app

being ignored accidentally.

### Docker Volume Debugging

List volumes
docker volume ls
Understand Compose volumes

Example:

ollama:
  volumes:
    - ollama-vol:/root/.ollama

Means:

Docker volume
      |
      v
/root/.ollama inside container
Remove containers but keep data
docker compose down
Remove containers AND volumes

⚠️ Deletes databases, Ollama models, etc.

docker compose down -v

### Ollama Debugging
Enter Ollama container
docker compose exec ollama sh
Check installed models
ollama list
Download a model
ollama pull llama3.2
Test model directly
ollama run llama3.2
Check Ollama storage
ls /root/.ollama

Models:

ls /root/.ollama/models
Check Ollama process
ps aux

Expected:

ollama serve
Check if Ollama server is already running
ollama serve

If you see:

bind: address already in use

Ollama is already running.

### Service-to-Service Networking Debugging
Check networks
docker network ls
Inspect a network
docker network inspect <network_name>
Test service name resolution

Inside a container:

ping <service_name>

Example:

ping ollama
Check environment variables inside container
env

or:

echo $VARIABLE_NAME

Example:

echo $OLLAMA_HOST

Expected:

http://ollama:11434

### Application Logs

Follow logs:

docker compose logs -f

#### Specific service:

docker compose logs -f webapp

#### Check errors after API calls.

API Testing

Test HTTP endpoint:

curl http://localhost:3000

PowerShell alternative:

Invoke-WebRequest http://localhost:3000

Check API response from Ollama:

curl http://ollama:11434/api/tags
Restarting After Code Changes

Restart only:

docker compose restart <service>

Rebuild after Dockerfile/code changes:

docker compose up --build

Full rebuild:

docker compose down
docker compose build --no-cache
docker compose up
Common Lessons
Container has old files?

Check:

docker compose exec <service> sh
ls
Frontend not updating?

Check:

cat public/index.html

inside container.

App cannot find files?

Check:

pwd

Working directory matters.

Container cannot connect to another service?

Check:

### Same Docker network

Use service name, not localhost

Example:

Correct:

http://ollama:11434

Wrong:

http://localhost:11434

