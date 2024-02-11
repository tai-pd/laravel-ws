FROM php:8.2-fpm

RUN apt-get update && apt-get install -y \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip \
    git \
    curl \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libwebp-dev

RUN docker-php-ext-configure gd --with-freetype --with-jpeg --with-webp \
    && docker-php-ext-install pdo pdo_mysql mbstring exif pcntl bcmath gd

# Cài Node.js và npm (nếu cần cho việc build assets)
RUN curl -sL https://deb.nodesource.com/setup_14.x | bash -
RUN apt-get install -y nodejs

# Cài đặt Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# RUN chown -R www-data:www-data /var/www/html/storage
# RUN chown -R www-data:www-data /var/www/html/bootstrap/cache

WORKDIR /var/www/html 
