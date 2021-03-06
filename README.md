# A tiny Docker PHP development environment.

## What should I do?

- Clone DNMP:

  > git clone https://github.com/lddsb/dnmp.git

- Run all containers:

  > docker-compose up -d

- Or run the containers what you like:

  > docker-compose up -d nginx mysql php-fpm7

## Features

- Have multiple versions of PHP
- Keep the latest version
- Easy to understand configuration files
- Flexible container collocation

## Directory Description

- `logs`: the log directory of the container.

- `mysql`: the build content directory of MySQL.

  - `conf`: path to configuration file for MySQL,like `my.cnf`
  - `data`: path to store database files.
  - *Dockerfile*: configuration the MySQL container.

- `nginx`: the build content directory of Nginx.

  - `conf`: virtual host configuration file configuration files and nginx configuration file.
  - *Dockerfile*: configuration the Nginx container.

- `php-fpm7`: the build content directory of PHP 7.1.x.
  - `conf` : just a php.ini here
  - *Dockerfile*: configuration the PHP container.

- `php-fpm5`: the build content directory of PHP 5.6.x.

  > similar to `php-fpm7`

## What should I do if I want to switch the PHP version?

> You can edit `php-fpm/Dockerfile` to change the [PHP version](https://hub.docker.com/_/php/) what you like.

## I need different PHP version for multiple project

- First

> you should build multiple PHP containers if you want different PHP version for multiple project.

- And then

> edit your virtual host configuration file and type the name of the PHP container.

- Finally

> It's OK now, enjoy it!

## I need more PHP extensions
> It's easy to add PHP extension if you use the `dnmp` , here we go

- First
> open the `Dockerfile` 

- And then
> add the extensions what you need like this
```
RUN docker-php-ext-install mbstring opcache pdo pdo_mysql mysqli
```

- Finally
> run this code on your terminal
```
docker-compose build && docker-compose up -d
```
> Enjoy it.
