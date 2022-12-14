# Docker - Laravel-project-management


A pretty simplified Docker Compose workflow that sets up a LEMP (Linux, NGINX, MySQL, PHP) network of containers for local Laravel development.

## Ports

Ports used in the project:
| Software | Port |
|-------------- | -------------- |
| **nginx** | 8080 |
| **phpmyadmin** | 8081 |
| **mysql** | 3306 |
| **php** | 9000 |
| **xdebug** | 9001 |
| **redis** | 6379 |

## Use

To get started, make sure you have [Docker installed](https://docs.docker.com/) on your system and [Docker Compose](https://docs.docker.com/compose/install/), and then clone this repository.

1. Clone this project:

   ```sh
   git clone https://github.com/AhmedMousa2020/docker-project-management.git
   ```

2. Inside the folder `docker-project-management` and Generate your own `.env` to docker compose with the next command:

   ```sh
   cp .env.example .env
   ```

3. You need **Create** or **Put** your laravel project in the folder source; to create follow the next instructions [Here](source/README.md).

4. Build the project whit the next commands:

   ```sh
   docker-compose up --build
   ```

---

## Remember

The configuration of the database **must be the same on both sides** .

```dotenv
# .env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=db_name
DB_USERNAME=db_user
DB_PASSWORD=db_password
DB_ROOT_PASSWORD=secret
```

```dotenv
# source/.env
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=db_name
DB_USERNAME=db_user
DB_PASSWORD=db_password
```

The only change is the `DB_HOST` in the `source/.env` where is called to the container of `mysql`:

```dotenv
# source/.env
DB_HOST=mysql
```

---

## larvel project Setup

To Down and remove the volumes we use the next command:

```sh
docker-compose down -v
```

Update Composer:

```sh
docker-compose run --rm composer update
```

Run compiler (Webpack.mix.js) or Show the view compiler in node:

```sh
docker-compose run --rm npm run dev
```
generate a key:

```sh
docker-compose run --rm artisan key:generate
```

Run all migrations:

```sh
docker-compose run --rm artisan migrate --seed
```

# addtional command

```sh
 php artisan
 php /var/www/html/artisan migrate:fresh --seed

 composer install 

 docker-compose run --rm npm install 
 docker-compose run --rm artisan clear:data
 docker-compose run --rm artisan cache:clear 
 docker-compose run --rm artisan view:clear 
 docker-compose run --rm artisan route:clear 
 docker-compose run --rm artisan clear-compiled 
 docker-compose run --rm artisan config:cache
 docker-compose run --rm artisan key:generate
 docker-compose run --rm artisan storage:link
 docker-compose run --rm artisan migrate --seed

 ```