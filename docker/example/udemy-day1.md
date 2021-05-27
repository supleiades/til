```sh
docker login
docker pull hello-world
docker images

docker run hello-world
docker ps -a

docker run -it ubuntu bash
docker restart {container_id/name}
docker attash {container_id/name}
# デタッチ
# Ctrl-p, Ctrl-q

docker commit 16aee20e14f1 ubuntu:updated
docker images
docker tag ubuntu:updated supleiades/first-repository
docker images
docker push supleiades/first-repository

docker rmi supleiades/first-repository
docker images
docker pull supleiades/first-repository
docker images
docker run -it supleiades/first-repository bash
```
