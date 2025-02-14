# syntax=docker/dockerfile:1

FROM php:8.2-cli

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
    intl \
    mysqli \
    pdo_mysql \
    zip \
    && docker-php-ext-enable \
    intl \
    mysqli \
    pdo_mysql \
    zip

# Limpa o cache para reduzir o tamanho da imagem
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Instala o Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Copia o código-fonte para o diretório de trabalho
COPY . /var/www

# Copia o arquivo php.ini personalizado
COPY docker/php/configs /usr/local/etc/php/conf.d