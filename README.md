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

## MySQL
### Switching from MySQL’s utf8 to utf8mb4

```
# Database
ALTER DATABASE database_name CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci;
# Table
ALTER TABLE table_name CONVERT TO CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
# Column
ALTER TABLE table_name CHANGE column_name column_name VARCHAR(191) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

## Varnish Cache - Fastly 

* `surrogate-key` has limits https://docs.fastly.com/guides/purging/getting-started-with-surrogate-keys
