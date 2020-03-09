# Docker examples

1. A docker container that prints Hello world! [LINK](./1-simplest/README.md)
2. A docker container that uses a bash script to print a message. [LINK](./2-simplest/README.md)
3. A docker container that uses nginx to host a static website. [LINK](./3-static-website/README.md)
4. A docker container that uses tensorflow to train a model and recognize flower images. [LINK](./4-tensor-flow/README.md)
5. A docker-compose that installs worpress and mysql and connects them. [LINK](./5-wordpress/README.md)

# Docker useful commands
```
> docker images
> docker rmi <image-id>
> docker container ls -a
> docker container rm <name>
> docker system prune -a                           # remove all unused objects
> docker ps -a                                     # running containers
> docker container stop $(docker container ls -aq) # stops all runing containers
```