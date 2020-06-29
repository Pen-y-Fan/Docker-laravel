# Docker For Laravel

Created from the blog [Containerize your Laravel Application with Docker Compose](https://webomnizz.com/containerize-your-laravel-application-with-docker-compose/?fbclid=IwAR102bITfIFEgp08JccBm5u1H0HRpyD2rGEcS7gGUuRqV4FppGJ-OXYh0I4)
 by Jogesh Sharma

This docker file will create a LAMP stack for local development:

1. **L**inux 
2. **A**pache
3. **M**ySQL - mysql:5.7
4. **P**HP - php:7.4.1-apache

## Step 1 – Download Laravel to your local machine

```shell script
laravel new project
```

Or.

```shell script
project.bat
```

## Step 2 – Create Docker Compose File

1. Copy the **Docker** folder from this repository, which contains the **Docker** and **vhost.conf** files
2. Copy the **docker-compose.yml** file

## Step 3 – Start Laravel Application with Docker Compose

Start Docker desktop and spin up the docker containers

```shell script
docker-compose up -d
```

## Step 4 – Laravel Database Connection in Docker

Edit the **.env** file.

```ini
...
DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=laraapp_db
DB_USERNAME=root
DB_PASSWORD=
...
```

**Note:** **DB_HOST** should be **db** instead of **localhost**

## Step 5 - Ignore the db directory

The MySQL database will create a db folder in the project root

Add the **db** directory to the file **.gitignore**:

```shell script
echo "db/" >> .gitignore
```

Will add **db/** to the file:

```text
...
db/
```

The local **db** data doesn't need to be added to git control.

## Step 6 - Add files to git

```shell script
git init
git add .
git status
git commit -m "Initial commit"
```
