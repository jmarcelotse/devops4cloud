docker container run
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