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

    docker container rm containerId or name (incase oof id just need the first 3 chars)

    docker container run --name containerName imageName (ex: nginx)
        ops:
            --publish 80:80 or 8080:80 para abrir a porta 80..
            --p 80:80 or 8080:80 para abrir a porta 80..

            --detach (para executar em background)
            --d

            -e MYSQL_RANDOM_ROOT_PASSWORD=yes (create a random password)
            -e MYSQL_ALLOW_EMPTY_PASSWORD=yes (let mysql password empty)

            -v mysql-db:/var/lib/mysql(create a volume with name mysql-db)
            -v /var/lib/mysql (create a new volume and attach it to the container)

        ex:
        docker container run -d --name mysql -e  MYSQL_ALLOW_EMPTY_PASSWORD=yes mysql

    docker container ls (exibir a lista de containers)
    docker container ls -a (exibir a lista de containers que n estao em execucao)

    docker image ls (exibir a lista de images)
    docker image ls -a (exibir a lista de images que n estao em execucao)

    docker container log containerName (ver os logs do container (pegar a senha do mysql que foi gerada por exmeplo))

    docker pull imageName - faz pull de uma imagem 
    docker container ps -a (Listar container process)

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
     docker container run --rm --net netName centos curl -s netAliasName:port 
        Creater a container with centos an run curl on the net alias name passed ith a port

## Image layer
docker image history imageName
docker image inspect imageName

## TAGS COMMANDS ##

	docker image tag --help
	docker image tag imageName newTag (claudiomelo/newTag) -> then: 
	docker image push claudiomelo/newTag (and it will be push to docker hub)
		Access denied: have to login:
			docker login
			docker logout

			cat .docker/config.json (check the auth key was add there)

## Docker. creating images ##

	docker build -f someDockerFile
		check docker file 1 of the project

	docker image build -t customTag (buil and image with a tag atacched to it)

## Docker file comands ##

	FROM nginx:latest (must be the first line of a docker file) getting the image (required)

	WORKDIR /usr/share/nginx/html -> it is a cd into the folder

	COPY filename filename

	RUN apt-get install something (executes comands on the image...)

	CMD - final comand on the image (required)
		if the docker file does not have a CMD it gets the CMD from the image on the FROM command

## Build own image ##


## Cleaning images ##
	Using Prune to Keep Your Docker System Clean (YouTube)
	You can use "prune" commands to clean up images, volumes, build cache, and containers. Examples include:

	- docker image prune to clean up just "dangling" images

	- docker system prune will clean up everything

	- The big one is usually docker image prune -a which will remove all images you're not using. Use docker system df to see space usage.

	Remember each one of those commands has options you can learn with --help.

	Here's a YouTube video I made about it: https://youtu.be/_4QzP7uwtvI

	Lastly, realize that if you're using Docker Toolbox, the Linux VM won't auto-shrink. You'll need to delete it and re-create (make sure anything in docker containers or volumes are backed up). You can recreate the toolbox default VM with docker-machine rm default and then docker-machine create

## Persistent Data Volumes ##
    docker volume prune (remove unused volumes)

    - named volumes


## Persistent Data Bind Mounting files ##
volume  local path:dockerPath
run -v /var/www/html:/var/www/html
$(pwd) - print the work directory
docker container run -d --name nginx -p 80:80 -v $(pwd):/usr/share/nginx/html nginx

## Docker Compose ##
