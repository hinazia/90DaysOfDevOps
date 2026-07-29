## MAIN Pointers

- Distroless container doesn't have sh, bash. This is actually one of the main characteristics of Distroless images
  and also makes it secure. so cant do `docker exec` and no one can change things inside.
- node_modules is the standard/default folder where npm installs packages.
- When copying a directory, the exact destination path matters.
   →  copy the contents into the current directory
   -> /app/node_modules → copy the directory as node_modules into that location

## Multi-Stage Builds
```
# Containers Working Directory
WORKDIR /app

# Copying the code from Host machine to the container
COPY . ./

# Install/RUN the Dependencies
RUN npm install

# Stage 02

FROM gcr.io/distroless/nodejs AS deployer

WORKDIR /app

# COPY --from=builder /app/node_modules .
COPY --from=builder /app/node_modules  /app/node_modules
COPY --from=builder /app/src/server.js /app/server.js

CMD ["server.js"]

```
