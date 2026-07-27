## Task 3: Two-Container Setup

Write a docker-compose.yml that runs:

  - A WordPress container
  - A MySQL container

´´´´
services:
  wordpress:
    depends_on: 
      - db
    image: wordpress:latest
    env_file:
      - .env
    ports:
      - 8000:80

  db:
    image: mysql:latest
    env_file:
      - .env
    volumes:
      - my-db-volume:/var/lib/mysql
    
volumes:
  my-db-volume:
  
 ´´´´   
