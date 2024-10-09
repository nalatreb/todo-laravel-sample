FROM php:8.2-fpm

# Alapcsomagok telepítése
RUN apt-get update && apt-get install -y \
    build-essential \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    locales \
    zip \
    jpegoptim optipng pngquant gifsicle \
    vim \
    unzip \
    git \
    curl \
    libonig-dev

# Composer telepítése
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Laravel szükséges kiterjesztések
RUN docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd

# Alkalmazás másolása
WORKDIR /var/www

# Jogosultság beállítása
RUN chown -R www-data:www-data /var/www

# Composer futtatás
# RUN composer install

EXPOSE 9000
CMD ["php-fpm"]