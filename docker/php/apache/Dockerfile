# syntax=docker/dockerfile:1

ARG PHP_VERSION
FROM php:${PHP_VERSION}-apache

WORKDIR /var/www

RUN apt-get update && apt-get install -y \
    libicu-dev \
    libzip-dev \
    libonig-dev \
    libssl-dev \
    zip \
    unzip \
    git \
    && docker-php-ext-install -j$(nproc) \
    mysqli \
    pdo_mysql \
    zip \
    && docker-php-ext-enable \
    mysqli \
    pdo_mysql \
    zip

# Limpa o cache para reduzir o tamanho da imagem
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Instala o Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Adiciona o caminho do Composer ao PATH
ENV PATH="/root/.composer/vendor/bin:${PATH}"

RUN composer global require laravel/installer

RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash

# Copia o código-fonte para o diretório de trabalho
COPY ./public /var/www

# Copia o arquivo php.ini personalizado
COPY docker/php/configs /usr/local/etc/php/conf.d

# Habilita o módulo de reescrita do Apache
RUN a2enmod rewrite

# Copia o arquivo de configuração do Apache
COPY docker/apache/vhost.conf /etc/apache2/sites-available/000-default.conf