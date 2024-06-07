## Installation

Install or clone your Laravel aplication inside this root. example: `dockerized-laravel/your-laravel`

Configure your database by changing `mariadb` environment inside `compose.yml`

Run this command below to start your Laravel, Nginx, and Mariadb container

```shell
docker compose up -d
```

\*use `sudo` if you need to run this as root user

After all containers is up, get in to your `php-fpm` container to install all dependencies and run your database migrations by running this command below

```shell
docker compose exec -it php-fpm sh
```

inside your container, run this command below to install all required dependencies

```shell
composer install
```

and then run this command below to run your migrations with the seeders

```shell
php artisan migrate --seed
```

## Directories and Files permissions

since UID:GID of `www-data` on Alpine Linux is **82** while on Ubuntu/Debian is **33**, you have to change directories and files owner on your Docker host to **82**, follow command line below to update your permissions.

\*note: `php-fpm` container on compose file is based on Alpine Linux

```bash
sudo chown -R $USER:82 storage/ bootstrap/
```

source: [stackoverflow.com](https://stackoverflow.com/questions/66507234/docker-volume-mount-and-permissions-www-data-on-host-33-becomes-xfs-33-in-a)

Contact: sysafarila.official@gmail.com
