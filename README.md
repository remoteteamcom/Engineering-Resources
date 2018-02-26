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

### Create User
```
CREATE USER 'newuser'@'%' IDENTIFIED BY 'password';
```

```
GRANT ALL PRIVILEGES ON mydatabase. * TO 'newuser'@'%';
```

```
FLUSH PRIVILEGES;
```

### Docker

#### Backup
docker exec CONTAINER /usr/bin/mysqldump -u root --password=root DATABASE > backup.sql

#### Restore
cat backup.sql | docker exec -i CONTAINER /usr/bin/mysql -u root --password=root DATABASE

## Caching

### Varnish Cache - Fastly 

* `surrogate-key` has limits https://docs.fastly.com/guides/purging/getting-started-with-surrogate-keys


## Cron

### Syntax
```
  # +---------------- minute (0 - 59)
  # |  +------------- hour (0 - 23)
  # |  |  +---------- day of month (1 - 31)
  # |  |  |  +------- month (1 - 12)
  # |  |  |  |  +---- day of week (0 - 6) (Sunday=0 or 7)
  # |  |  |  |  |
  # *  *  *  *  * 
```
