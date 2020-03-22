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
3. `cd` into  `src` folder and edit `env` file
4. Download bedrock with composer:

```
docker-compose run composer create-project roots/bedrock
````
or if you have composer installed globally:

```
composer create-project roots/bedrock
```

5. `cd` into `bedrock` folder and rename `web` folder to  `html`
6. `cd` into `config` folder and in `application.php` change `$webroot_dir` variable from `web` to `html`
7. copy `env` file from `src` folder to `bedrock` and rewrite. 
8. `cd into the root folder and run:
```
docker-compose up -d
```

9. Wordpress is ready for installation on the localholst IP you entered in `.env.` file. 



