## Installation
- Install your laravel aplication inside this root. example: `dockerized-laravel/laravel`
- run `docker compose up -d` to start your docker containers
- access PHP-FPM container by typing `docker compose exec -it php-fpm sh`, then you can use composer command here like `php artisan migrate`