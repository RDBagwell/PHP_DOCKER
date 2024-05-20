FROM php:8-fpm

# Replace shell with bash so we can source files
SHELL ["/bin/bash", "-c"]

ENV DEBIAN_FRONTEND=noninteractive

# Install system dependencies
RUN apt-get update && apt-get install -y \
    gcc \
    mono-mcs \
    libssh2-1-dev \
    libssh2-1 \
    zip \
    unzip \
    vim \
    wget \
    git \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libwebp-dev \
    libicu-dev \
    libxml2-dev \
    libzip-dev \
    && rm -rf /var/lib/apt/lists/* \
    && apt-get clean

# Install GD extension
RUN docker-php-ext-configure gd --with-freetype --with-jpeg && \
    docker-php-ext-install -j$(nproc) gd

# Install PHP extensions
RUN docker-php-ext-configure intl && \
    docker-php-ext-install intl pdo pdo_mysql mysqli soap zip && \
    pecl install ssh2-1.3.1 && \
    docker-php-ext-enable ssh2 && \
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

CMD ["php-fpm"]