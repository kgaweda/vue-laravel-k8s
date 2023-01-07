FROM php:8.1.13-apache-bullseye

RUN apt-get update && apt-get install git -y zip libzip-dev

RUN docker-php-ext-install zip

WORKDIR /var/www

COPY --from=composer:2.2.18 /usr/bin/composer /usr/bin/composer

COPY ./laravel/docker/000-default.conf /etc/apache2/sites-available/000-default.conf

COPY ./laravel /var/www

RUN composer install

RUN chown -R www-data:www-data /var/www

RUN a2enmod rewrite