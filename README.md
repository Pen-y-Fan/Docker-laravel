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
git clone https://github.com/laravel/laravel.git laravelapp
```

Or if composer is installed locally and laravel globally:

```shell script
laravel new laravelapp
```

## Step 2 – Create Docker Compose File

1. Copy the **Docker** folder from this repository, which contains the **Docker** and **vhost.conf** files
2. Copy the **docker-compose.yml** file

e.g. from the root 

```shell script
cd C:\laragon\www
xcopy Docker-laravel\.docker\*.* laravelapp\.docker\ /d /y
xcopy Docker-laravel\docker-compose.yml laravelapp\ /d /y
```

## Step 3 – Start Laravel Application with Docker Compose

Start Docker desktop and spin up the docker containers

```shell script
cd laravelapp
docker-compose up -d
```

## Step 4 – Laravel Database Connection in Docker

Edit the **.env** file.

```shell script
copy .env.example .env /b
```

```ini
...
DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=laraapp_db
DB_USERNAME=root
DB_PASSWORD=
....
```

**Note:** **DB_HOST** should be **db** instead of **localhost**

## Step 5 - Ignore the db directory

The MySQL database will create a db folder in the project root

Add the **db** directory to the file **.gitignore**:

```shell script
echo db/ >> .gitignore
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
git status
git add .
git commit -m "Initial commit"
```

## Using composer

The docker image for Laravel includes php and composer, to access composer, list the running docker containers:

```shell script
docker ps
```

Connect to the container with the name **laravelapp** (set in docker-compose.yml), by its container ID

e.g.

```shell script
docker exec -it 83ad4ef2b5dc bash
``` 

You can now use composer and php commands:

```shell script
composer install
php artisan key:generate
```

## Web site

To view the website open the browser to: <localhost:8080>

The port **8080** is also set in **docker-compose.yml**
