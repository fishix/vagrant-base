FROM php:7.0.2-fpm

RUN echo "date.timezone=UTC" > /usr/local/etc/php/conf.d/docker-php-ext-datetime.ini

RUN docker-php-ext-install pdo pdo_mysql

WORKDIR /var/www/symfony
