# WP Bedrock and Docker
Simple and fast Wordpress Bedrock setup on docker.

## Supported technologies
- Apache 
- PHP 7.3
- MySQL 8
- PhpMyAdmin
- Composer

## Installation

1. Clone this repository to your PC
2. `cd` into the folder and edit `.env` 
3. `cd` into  `src` folder and edit `.env`
4. Download bedrock with composer:

```
docker-compose run composer create-project roots/bedrock
````
or if you have composer installed globally:

```
composer create-project roots/bedrock
```

5. copy `env` file from `src` folder to `bedrock` and rewrite. 

6. From the root run:
```
docker-compose up -d
```

7. Wordpress is ready for installation on the localholst IP you have inserted in `.env` file.


## MySQL

Database dump:

```
docker exec CONTAINER-NAME sh -c 'exec mysqldump DBNAME -uroot -p"$MYSQL_ROOT_PASSWORD"' > backup.sql
```

Database import:

```
docker exec -i CONTAINER-NAME sh -c 'exec mysql -uroot DBNAME -p"$MYSQL_ROOT_PASSWORD"' < backup.sql
```

## Additional settings

### Apache DOCUMENT ROOT change

If you want to change the default web folder, just rewrite these 3 files:

1. In `bedrock` folder rename `web` folder to  `html` for instance
2. In `config` folder in `application.php` change `$webroot_dir` variable from `web` to `html`
3. In `Dockerfile` change `APACHE_DOCUMENT_ROOT`


