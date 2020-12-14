# Docker

## Delete all containers

```
sudo docker rm $(sudo docker ps -a -q)
```

## Delete all images

```
sudo docker rmi $(sudo docker images -q)
```

## Attach

```
sudo docker exec -it <mycontainer> bash
```

## Remove all networks

```
sudo docker network rm $(sudo docker network ls)
```


## Remove unused data

```
docker system prune -a
```


## Remove build cache

```
docker builder prune -a
```


## Remove unused images

```
docker image prune -a
```
