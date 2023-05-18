GRPC

API Gateway

HATEOAS


https://landscape.cncf.io/

https://github.com/maciejkra/k8s

docker run -it krajewskim/mc

https://docs.docker.com/engine/reference/builder/

docker rm -f $(docker ps -q)
docker rm -f $(docker ps -qa)
docker image rm -f $(docker image ls -q)
https://docs.docker.com/get-started/docker_cheatsheet.pdf



docker diff

docker top contID

docker stats

coker cp <ContID>:/etc ./

docker run -p 80:80 -v ${PWD}:/usr/share/nginx/html -d nginx
#host has folder - copied to docker
#host has no folder - copied from docker

dockeer volume ls

===============
docker run -p 80:80 -v www_data:/usr/local/apache/httpdoc/...

