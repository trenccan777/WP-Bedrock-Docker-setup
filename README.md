# WP Bedrock and Docker
Simple and fast Wordpress Bedrock setup on docker. This setup has the advantage of using separate container for each service which is little bit slower on Windows devices. Faster version of this setup using official WordPress image is [here](https://github.com/trenccan777/wordpress-bedrock-docker-boilerplate/). 

## Supported technologies
- Apache 
- PHP 7.3
- MySQL 8
- PhpMyAdmin
- Composer
- WP-CLI - command line interface for WordPress

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

## WP-CLI

To use wp-cli, you can easily set alias in `.bashrc` file in your user folder. 

```
alias wp="docker-compose run --rm wpcli"
```

Then you can run standard commands. For instance for database manipulation you can run:

Import database:
``` 
wp db import databasename.sql
```

Database dump:

```
wp db export
```

Database drop:

```
wp db drop
```

Search and replace:

```
wp search-replace 'old-url' 'new-url'
```

## MySQL

If you want, you can use standard MySQL commands. 

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


