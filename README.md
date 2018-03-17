# Craft CMS 3 (RC-15) + Docker

About CraftCMS : https://github.com/craftcms  
Download Docker : https://www.docker.com/community-edition#/download

## Quickstart
- Configure env: `$ cp .env.example .env` 
- Start container: `$ docker-compose up -d` 
- Enter container: `$ docker-compose exec php bash` 
    - `$ composer install` 
    - `$ craft install` 
    - `$ craft migrate/up` (optional, generates a homepage & mail settings)

Website : `http://localhost:8084` (/admin to access Craft admin)
PhpMyAdmin : `http://localhost:8085`  
Mail catcher : `http://localhost:8086`  
Logs : `docker/volumes/nginx`

## Customize PHP image
The PHP image is host on Docker Hub because first build takes a long time.  
You can use your own custom version by modifying your docker-compose.yml.
```yml
services:
    php:
        build:
            context: ./docker/php
```

### Release new version on Docker Hub
- `$ docker build -t atillay/craftcms3-php ./docker/php` 
- `$ docker push atillay/craftcms3-php` 