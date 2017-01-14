# Docker WordPress setup

This setup contains Apache, PHP 7.1, MariaDB and WP-CLI.

## First time setup

If you're using this for the first time on your computer, create an image using the Dockerfile.

Use the docker build command to create the image.

`docker build -t customhttpd:basic .`

Notes: 

* Change the Dockerfile to your needs if you need special PHP modules, Apache settings, etc. Change the tag 'basic' into something that reflects your changes.

* If you used a different name and/or tag, change that in docker-compose.yml.

## Running the dev environment

If you've already built the container you only need the docker-compose.yml file in your project.

To start the development environment run:

`docker-compose up`

Running WP-CLI commands:

`docker-compose run wpcli db dump`

If you want to reset your development setup, run:

`docker-compose down`

## Connecting to the database

Use these settings to connect WordPress to the database:

`
DATABASE: wordpress
USER: wordpress
PASSWORD: wordpress
HOST: wp
`

If you want to administer the DB using a GUI on the host computer, use these settings:

`
USER: root
PASSWORD: root
HOST: localhost
`

## Requirements
Docker 1.10.0 +