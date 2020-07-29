# docker-laravel-setup

Docker setup for local Laravel development - inspired by [@aschmelyun ](https://dev.to/aschmelyun)

## Major skills acquired
With this Docker setup, i was able to ground my skills in some previous knowledge i had already acquired when learning DevOps with Docker. Some of the skills includes:

- Running Docker Containers
- Creating a Docker image either directly from the command-line (using docker command-line tools) or through a Dockerfile
- creating Networks in Docker
- nginx custom server configuration for Docker Compose
- Using Docker Compose (docker-compose.yml) as a config file for carrying multiple Docker containers connected through a network


If you are also interested in setting up docker for laravel development, visit this [link](https://dev.to/aschmelyun/the-beauty-of-docker-for-local-laravel-development-13c0) on dev.to. It's a comprehensive explanation on docker for local laravel development written by [@aschmelyun ](https://dev.to/aschmelyun)

For help getting started with Docker, view Docker's
[online documentation](https://docs.docker.com/), which will help get you up to speed with Docker.

Moreover, if you want to use the setup in this repo, follow these instructions:

### clone the repo

```bash
git clone git@github.com:duixe/docker-laravel-setup
```

## Run docker-compose, del public dir, and install laravel

```bash
# make sure you're in the root dir
docker-compose up -d -- build
# traverse into the src dir
cd src/
# delete public folder
rm -r public
# install laravel into the src directory
composer create-project laravel/laravel
```

## Available commands for laravel development

```bash
# run composer and install any third party package needed
docker-compose run -rm composer require "package_name/packge"
# run npm to install any front-end dependencies needed
docker-compose run -rm npm install
# package all front-end dependencies with laravel-mix
docker-compose run -rm npm run dev
# you can also run artisan commands e.g php artisan migrate will be 👇
docker-compose run -rm artisan migrate
```

## exit the docker-compose daemon running in background

```bash
docker-compose down
```

## Note

Make sure you have docker and docker-compose installed on your computer, for help on how to install both docker and docker-compose visit docker's [online documentation](https://docs.docker.com/).

If you are on linux you might need to start the docker service before running any docker-compose commands

```bash
service docker start
# or
systemctl docker start
```

If there is any error with regards to PDO or MySQL, be sure to change the env variables of mysql in the ***docker-compose.yml*** file to suit your env variables in laravel ***.env*** file.
