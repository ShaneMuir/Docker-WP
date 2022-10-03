# Docker WP
Within this repo there is a simple docker-compose.yml setup to get up and running with a WordPress
installation without the requirement to install anything other than docker desktop.

[Download Docker](https://www.docker.com/products/docker-desktop/)

There is 3 services being used for now, which are mariaDB for the database, WordPress Core (latest) 
and phpMyAdmin tool for managing the database we may add to this later as we build on docker for WordPress

## Getting Started
To get up and running with Docker desktop and WordPress you will need to download the 
`docker-compose.yml` file to your root directory.

### New WordPress Installation

After Docker Desktop is installed onto your machine you can run
```
docker-compose up -d
```
to run your containers in detached mode make sure you have no other services exposing the ports
we have defined in our docker-compose file.

Once the containers are up and running you can navigate to `http://localhost/` and proceed with the new 
installation of WordPress

### Existing WordPress Installation

After Docker Desktop is installed, you can git clone your project into your directory and then run
```
docker-compose up -d
```
to run your container in detached mode make sure you have no other services exposing the ports
we have defined in our docker-compose file. 

Next we need to navigate to phpMyAdmin and upload the existing project's database to our new database.

Export your existing project's database locally onto your machine and then use the import functionality of 
phpMyAdmin to import the existing database into our new database for our WordPress installation.

As per any existing site migration with WordPress you will need to update your `wp_options` table so that
`siteurl` and `home` options point to your new domain (https://localhost/).

Otherwise, you can use any sql client of your choice to connect to the database container using the port exposed
within the docker-compose file. I've used `port 3308` to connect externally using a sql client you can use the below 
details;

- host: 127.0.0.1
- username: root
- password: yourpassword
- port: 3308

Once you have import your database you can navigate to https://localhost/ and check if everything is up and running

Any issues - [google](https://google.com/) them... Happy coding
