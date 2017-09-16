# My Cheatsheets
There are lots of cheatsheets in github. This is just what i needed as a backend developer.


## Docker

### Delete all containers

```
sudo docker rm $(sudo docker ps -a -q)
```

### Delete all images

```
sudo docker rmi $(sudo docker images -q)
```

### Attach

```
sudo docker exec -it <mycontainer> bash
```

### Remove all networks

```
sudo docker network rm $(sudo docker network ls)
```
