## ApOgEE Docker Container Setup for Codeigniter 3 Development

I will add docker compose file to simplify my task here.

### Install Codeigniter 3
```
composer create-project codeigniter/framework apogee-phpci3
```

### Clone CI3 Project


### Database Setup

Enter mysql docker container
```
docker exec -it < container > /bin/bash
```

You will get the root prompt. connect to mysql using command line and enter root password as per `docker-compose.yml`

```
mysql -p 
```

In the mysql prompt, run this to create database and database user.

```
CREATE SCHEMA namadb;
CREATE USER 'dbuser' IDENTIFIED BY 'passwordkau';
GRANT ALL PRIVILEGES ON `namadb` . * TO 'dbuser';
FLUSH PRIVILEGES;
```

#### Backup & Restore

```
# Backup
docker exec CONTAINER /usr/bin/mysqldump -u root --password=root DATABASE > backup.sql

# Restore
cat backup.sql | docker exec -i CONTAINER /usr/bin/mysql -u root --password=root DATABASE

```

