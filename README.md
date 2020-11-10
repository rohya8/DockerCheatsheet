# DockerCheatsheet

--- Docker version ---  \
docker –version

--- Search docker image ---  \
docker search <search term>

--- Docker image ---  \
docker pull <image name>

--- Docker list all images ---  \
docker images

--- Docker list containers ---  \
docker ps (list of running container(s))  \
docker ps -a ( stopped containers(	))  \

---Docker copy to and from container ---  \
docker cp <container>:/usr/src/app/config.json .  \
  
docker cp config.json <container>:/usr/src/app/config.json  \
  
docker exec -ti <container> /bin/ash  \
  

--- Docker Save and Load commands---  \
docker save project_name > project_name.tar  \

docker load --input project_name.tar  \

--- Docker build ---  \
docker build -t project_name .  \

--- Docker Run with no container ---  \

docker network create my-network  \

docker run --net=my-network --name mymongo -p 27017:27017 -d mongo  \

docker run -it --net=my-network --name project_name  --rm -p 3113:3113 -d project_name  \


--- Docker Run ---  \

docker network create my-network  \

docker run --net=my-network --name mymongo -p 27017:27017 -d mongo  \

docker run --net=my-network --name project_name -p 3113:3113 -p 80:80 -d project_name  \

# important commands

kubectl exec -it <mongodbcontainer> -- /bin/bash \
mongo \
show databases \
use <dbname> \
db.dropDatabase() \
db.<collectionname>.drop() \
