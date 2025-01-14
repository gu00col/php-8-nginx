FROM php:8.0-fpm

WORKDIR /var/www

RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libpq-dev \
    libsqlite3-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd \
    && docker-php-ext-install mysqli pdo pdo_mysql pdo_pgsql pdo_sqlite

# Instala o Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

COPY . /var/www

# Copiar arquivo php.ini
COPY docker/php/php.ini /usr/local/etc/php/php.ini

EXPOSE 9000

CMD ["php-fpm"]
