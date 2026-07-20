### Main Pointers

- /bin/sh in "docker exec -it <container id> <shell>" when using alpine image instead of ubuntu
- alpine is light weight and does not have bash installed. It was basic sh shell built-in
- CMD to keep chnaging the input in images
- ENTRYPOINT to hard code the arguments
-   
