## Day 34 – Docker Compose File: Real-World Multi-Container Apps

```
services:
  webapp:
    build: .
    depends_on:
      postgres_db:
        condition: service_healthy
    ports:
      - 5000:5000
    networks:
      - flask-app-nw

  postgres_db:
    image: postgres
    environment:
      - POSTGRES_PASSWORD=mysecretpassword
    ports:
      - 5432:5432
    healthcheck:
      test: ["CMD", "pg_isready", "-U", "postgres"]
      interval: 30s
      timeout: 10s
      retries: 3
      start_period: 40s
    restart: always
    volumes:
      - my-postgres-volume:/var/lib/postgresql/data
    networks:
      - flask-app-nw

  cache:
    image: redis

volumes:
  my-postgres-volume:

networks:
  flask-app-nw:
    driver: bridge

```

- Write in your notes: Why doesn't simple scaling work with port mapping?
  Because multiple containers cannot bind to the same host port at the same time.
  If you scale a service to three containers while mapping the same host port, Docker will get a port binding error.
  Key idea: The containers can all listen on their own container port (8000), but the host port (8080) can only be bound once.
