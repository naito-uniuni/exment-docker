FROM php:8.2-fpm

# 依存ライブラリのインストール
RUN apt-get update && apt-get install -y \
    git wget unzip libxml2-dev libpng-dev libzip-dev libonig-dev default-mysql-client \
    && docker-php-ext-install pdo_mysql mbstring dom gd zip

# Composerインストール
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/exment

RUN { \
    echo 'memory_limit = 512M'; \
    echo 'max_input_vars = 3000'; \
    echo 'upload_max_filesize = 100M'; \
    echo 'post_max_size = 100M'; \
    echo 'max_execution_time = 300'; \
    } > /usr/local/etc/php/conf.d/exment.ini
