```
docker container run
```
```
docker container run hello-world
```
```
docker container ls
```
```
docker container ls -a
```
```
docker container run --name meucontainer hello-world
```
```
docker container rm meucontainer
```
```
docker container rm 836b069a4fc2
```
```
docker container run -it ubuntu /bin/bash
```
```
docker container run nginx
```
```
docker container run -d nginx
```
```
docker container exec -it d8f9fad941d9 /bin/bash
```
```
docker container run -d -p 8080:80 nginx
```
```
docker container stop 21141f80caa2
```
```
docker container rm -f $(docker container ls -qa)
```
```
docker build -t conversao-distancia -f Dockerfile .
```
```
docker build -t conversao-distancia -f Dockerfile --no-cache .
```
```
docker image ls
```
```
docker image rm d2c94e258dcb
```
```
docker container run -d -p 8181:5000 conversao-distancia
```
```
docker build -t jmarcelotse/conversao-distancia:v1 -f Dockerfile .
```
```
docker image prune
```
```
docker login
```
```
docker push jmarcelotse/conversao-distancia:v1
```
```
docker tag jmarcelotse/conversao-distancia:v1 jmarcelotse/conversao-distancia:latest
```
```
docker image ls
```
```
docker push jmarcelotse/conversao-distancia:latest
```
```
docker system prune -a --volumes
```
```
docker container run -d -p 8282:5000 jmarcelotse/conversao-distancia:v1
```
```