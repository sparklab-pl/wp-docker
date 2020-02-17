# WP Docker
This is a boilerplate for WordPress project with local development environment based completely on Docker.

## Remote Local Development
Also to avoid slow file sync between container and host on Windows and Mac,
this environment assumes "remote" development locally.
Application code is copied into the container. Developer accesses the code 
as if it was on the remote machine and sync changes made locally.

* When using PHPStorm it can be conveniently setup using Deployments option with [auto sync](https://www.jetbrains.com/help/phpstorm/uploading-and-downloading-files.html#automaticUploadOnUpdate) enabled.
* With VS Code use [Remote Containers extension](https://code.visualstudio.com/docs/remote/containers).

## Requirements
* Docker
* docker-compose

## Configure .env
Copy .env.example to .env file. Most important settings are:
HTTP_PORT - this is the localhost port on which the app will be listening
SSH_PORT - this is localhost ort on which you can ssh to the container to sync files
SSH_PASSWORD - password for the app user to ssh

## Launch docker
```
docker-compose up -d
```

## Install composer dependencies
```
./scripts/composer-install.sh
```

## Install WordPress
```
./scripts/wp.sh core install --url=localhost:8008 --title="Wordpress Blog" --admin_user=local.admin --admin_password=local.password --admin_email=admin@localhost.example
```

## Scripts
Scripts folder contains convenient scripts for common tasks and running commands in Docker containers.
* wp.sh - run a WP CLI command
* wp-cli.sh - run a command in PHP CLI container
