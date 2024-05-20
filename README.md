# Dockerized ecommerce   

### Installation  
**Download the latest version of Docker Desktop**
[https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/)  
Select the platform to install it on. Follow the install instructions.

**(Optional) Check if docker and docker-compose are installed.**  
```bash
docker --version
```
```bash
docker-compose --version
```
**Clone the docker repo to your "Projects" folder**
**Rename .env_copy to .env**  
Add your credentials to the appropriate variables.
```.env
# exapmple
MYSQL_ROOT_PASSWORD=your_root_password
MYSQL_USER=your_mysql_username
MYSQL_PASSWORD=your_mysql_password
PATH_TO_PROJECT_DIR=../
```  

**Add 00-init.php file to ./{site folder}/dist/config/ use the credentials added in the .env file**
**In 00-int.php file change $_['db_host'] = 'localhost' to $_['db_host'] = 'mysql'**  
**Add sql dump files to ./install/ in the docker folder**  

**(On initial setup. Skip if already done) cd into /{site folder}/dist/**
Install composer dependencies 
```bash
composer install 
```

**cd into the root directory the directory with the file _docker-compose.yml_ file in it.**  
```bash
docker-compose up -d --build
#or 
docker compose up -d --build
```
Allow the database to finish populating. Depending on the size of the dumps this can take 30+ minutes.  
You should be all set up now. Use the URL  
For ecommerce http://localhost:8080  
For brandloudr-admin http://localhost:8081  
For bootcamp http://localhost:8082  


**After initial installation you just need you can just run**  
```bash
docker-compose up -d
#or 
docker compose up -d
```
to start it up and
```bash
docker-compose down
#or 
docker compose up -d
```
to shut it down

### Reinstalling your database.   
**If you need to reinstall your database run**
```bash
docker-compose down --rmi "all" -v
#or 
docker compose down --rmi "all" -v
```  
This command will remove all docker containers, images, and volumes.  

**Add or replace the msql dumps for you database you need.**  
next  
```bash
docker-compose up -d --build
#or 
docker compose up -d --build
```
Allow the database to finish populating.  

**The default admin login is**
```
admin@buckedup.com
admin
```

## Commands to know:
```
# Starts existing containers for a service.
docker-compose start

# Stops running containers without removing them.
docker-compose stop

# Pauses running containers of a service.
docker-compose pause

# Unpauses paused containers of a service.
docker-compose unpause

# Lists containers.
docker-compose ps

# Builds, (re)creates, starts, and attaches to containers for a service. Adding -d or --detach will run docker in the background
docker-compose up

# Stops containers and removes containers, networks, volumes, and images created by up.
docker-compose down

# To see all running containers
docker ps

# To get inside a running container
docker exec -it CONTAINERNAME/CONTAINERID bash
```