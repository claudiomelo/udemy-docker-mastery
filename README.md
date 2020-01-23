# Udemy Course Docker Mastery: with Kubernetes+Swarm from a Docker Captain

> Build, test, deploy containers with the best mega-course on Docker, Kubernetes, Compose, Swarm and Registry using DevOps

This repo is for use in my Udemy Courses "Docker Mastery" and "Swarm Mastery"

Get these courses for with my "cheapest on the Internet" coupon links:

https://www.bretfisher.com/courses

My other DevOps and Docker resources are at https://www.bretfisher.com/docker

Feel free to create issues or PRs if you find a problem with examples in this repo!

## Commands ##

    docker container start containerName

    docker container stop containerName

    docker container run imageName (ex: nginx)
        ops:
            --publish 80:80 or 8080:80 para abrir a porta 80..
            --p 80:80 or 8080:80 para abrir a porta 80..

            --detach (para executar em background)
            --d

            -e MYSQL_RANDOM_ROOT_PASSWORD=yes (create an enviriment variable)

    docker container ls (exibir a lista de containers)
    docker container ls -a (exibir a lista de containers que n estao em execucao)

    docker image ls (exibir a lista de images)
    docker image ls -a (exibir a lista de images que n estao em execucao)

    docker container log containerName (ver os logs do container)

    docker pull imageName - faz pull de uma imagem 

## Cli Monitoring and inspecting ##
    Docker container top containerName or ID
    Docker container inspect containerName or ID
    Docker container stats containerName or ID


## Getting a Shell Inside Containers: No Need for SSH ##
    docker container run --it (create new container interactivily)
    docker container run --ai (start a container and enter on it interactivily)
    docker container run --it --name nginx nginx bash (cria um container chamado nginx com nginx e abre o bash `terminal` dentro do container)
    docker container run exec --it (run aditional command in existing container)
    docker container exec --it mysql bash(enter on the bash of a running container called mysql)


## Docker networks - private and public Comms for containers ##
    docker network ls
    docker network inspect
    docker network create --driver
    docker network connect
    docker network disconnect


## Docker networks - DNS ##
    docker run -d -net netName --net-alias netAliasName elasticsearch:2 (image with version 2)
        Creates a contaner attached to a network with an alias an elasticsrach image v2
    docker container rum --rm --net netName alpine nslookup netAliasName
        Creater a container with alpine an run nslookup on the net alias name passed
     docker container rum --rm --net netName centos curl -s netAliasName:port 
        Creater a container with centos an run curl on the net alias name passed ith a port

## Image layer
docker image history imageName
docker image inspect imageName
 



