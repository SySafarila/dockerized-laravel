## Installation and Usage

Install or clone your Laravel aplication inside this root. example: `dockerized-laravel/your-laravel`

Configure your database by changing `mariadb` environment inside `compose.yml`

Run this command below to start your Laravel, Nginx, and Mariadb container

```shell
docker compose up -d
```

\*use `sudo` if you need to run this as root user. Or, check this [docs](https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user) to run docker with non-root user

After all containers is up/running, login to your `php-fpm` container to install all dependencies by running this command below:

```shell
docker compose exec -it php-fpm sh
```

inside your container, run this command below to install all required dependencies

```shell
composer install
```

after all dependencies are installed, run this command below inside your to run your database migration

```shell
php artisan migrate:fresh --seed
```

## Directories and Files permissions

Since UID:GID of `www-data` on Alpine Linux is **82** while on Ubuntu/Debian is **33**, you have to change directories and files owner on your Docker host to **82**, follow command line below to update your permissions.

\*note: `php-fpm` container on compose file is based on Alpine Linux

```bash
sudo chown -R 82:$USER storage/ bootstrap/
```

\*run this command on your ROOT laravel folder. Source: [stackoverflow.com](https://stackoverflow.com/questions/66507234/docker-volume-mount-and-permissions-www-data-on-host-33-becomes-xfs-33-in-a)

## CronJob or Automation

Run this command below to apply queue for a minute

```sh
crontab mycrontab
```

Make sure all files on `shell-scripts` folder are executable for your user.

## Non-root Docker

Read this [Documentation](https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user) to run your docker without `sudo`

## SSL Configuration Reference
- [How To Host a Website Using Cloudflare and Nginx on Ubuntu 20.04 - DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-host-a-website-using-cloudflare-and-nginx-on-ubuntu-20-04)