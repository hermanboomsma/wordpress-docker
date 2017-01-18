# WordPress Docker setup

This setup contains Apache, PHP 5.6 or PHP 7.1, MariaDB, WP-CLI and PHPMyAdmin.

## First time setup

If you're using this for the first time on your computer, create an image for Apache and PHP using one of the Dockerfiles found in the Dockerfiles directory.

If you want to use PHP 7.1, use the docker build command to create the image from the Dockerfile supplied:

`docker build -t apachephp:7.1 Dockerfiles/apachephp7.1`

Change 7.1 into 5.6 if you want to use PHP 5.6. 

`docker build -t apachephp:5.6 Dockerfiles/apachephp5.6`

The PHP 5.6 version has the MySQL driver as well as the MySQLi driver for backwards compatibility. This should work for older projects.

Notes: 

* Change the Dockerfile to your needs if you need special PHP modules, Apache settings, etc. Change the tag '7.1' into something that reflects your changes, like '7.1-256M' if you change the PHP memory limit to 256Mb.

* You are free to choose the name and tag that are set with the -t paramter. Set the same name/tag in docker-compose.yml.

## Running the dev environment

If you've already built the container you only need the docker-compose.yml file in your project.

Set the PHP version you want to use. Change `image: apachephp:7.1` in `image: apachephp:5.6` if you want to use PHP 5.6. No need to change anything if you want to use PHP 7.1.

To start the development environment run:

`docker-compose up`

Running WP-CLI commands:

`docker-compose run wpcli db dump`

If you want to reset your development setup, run:

`docker-compose down`

## Connecting to the database

Use these settings to connect WordPress to the database:

```
DATABASE: wordpress
USER: wordpress
PASSWORD: wordpress
HOST: db
```

PHPMyAdmin runs on port 81. Use these credentials:

```
USER: root
PASSWORD: root
HOST: db
```

If you want to administer the DB using a GUI on the host computer, use these settings:

```
USER: root
PASSWORD: root
HOST: localhost
```

## Tips

* Apache and PHP logs are stored in ./_log

## Requirements
Docker 1.10.0+