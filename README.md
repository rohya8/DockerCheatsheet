# DockerCheatsheet

--- Docker version ---
docker –version

--- Search docker image ---
docker search <search term>

--- Docker image ---
docker pull <image name>

--- Docker list all images ---
docker images

--- Docker list containers ---
docker ps (list of running container(s))
docker ps -a ( stopped containers(	))

---Docker copy to and from container ---
docker cp <container>:/usr/src/app/config.json .
docker cp config.json <container>:/usr/src/app/config.json
docker exec -ti <container> /bin/ash

--- Docker Save and Load commands---
docker save boxoffice-boxofficeui > boxoffice-boxofficeui.tar
docker save boxoffice-boxofficecore > boxoffice-boxofficecore.tar
docker save exela/ingester > ingester.tar
docker save exela/exela-auth > exela-auth.tar


docker load --input boxoffice-boxofficeui.tar
docker load --input ingester.tar
docker load --input exela-auth.tar

--- Docker build ---
docker build -t boxoffice/boxofficeui .
docker build -t boxoffice/boxofficecore .
docker build -t exela/ingester .
docker build -t exela/exela-auth .

---Docker Run with no container---
docker network create my-network
docker run --net=my-network --name mymongo -p 27017:27017 -d mongo
docker run -it --net=my-network --name boxoffice-boxofficeui  --rm -p 3113:3113 -d boxoffice/boxofficeui

docker network create my-network
docker run --net=my-network --name mymongo -p 27017:27017 -d mongo
docker run -it --net=my-network --name boxoffice-boxofficecore  --rm -p 3112:3112 -d boxoffice/boxofficecore

docker network create my-network
docker run --net=my-network --name mymongo -p 27017:27017 -d mongo
docker run -it --net=my-network --name ingester  --rm -p 3001:3001 -d exela/ingester	

docker network create my-network
docker run --net=my-network --name mymongo -p 27017:27017 -d mongo
docker run -it --net=my-network --name exela-auth  --rm -p 3001:3001 -d exela/exela-auth	



---Docker Run---
docker network create my-network
docker run --net=my-network --name mymongo -p 27017:27017 -d mongo
docker run --net=my-network --name boxoffice-boxofficeui -p 3113:3113 -p 80:80 -d boxoffice/boxofficeui

docker network create my-network
docker run --net=my-network --name localhost -p 27017:27017 -d mongo
docker run --net=my-network --name boxoffice-boxofficecore -p 3112:3112 -d --env-file env-local.properties boxoffice/boxofficecore

docker network create my-network
docker run --net=my-network --name mymongo -p 27017:27017 -d mongo
docker run --net=my-network --name ingester -p 3001:3001 -d  --env-file env-local.properties exela/ingester	

docker network create my-network
docker run --net=my-network --name mymongo -p 27017:27017 -d mongo
docker run --net=my-network --name exela-auth -p 3110:3110 -d --env-file env-local.properties exela/exela-auth	


#important commands
kubectl exec -it <mongodbcontainer> -- /bin/bash
mongo
show databases
use <dbname>
db.dropDatabase()
db.<collectionname>.drop()
