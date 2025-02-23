# ./docker/backend/Dockerfile
FROM php:8.3-apache

# Composer doesn't like the root user!
ARG COMPOSER_ALLOW_SUPERUSER=1

# Install system dependencies
RUN    apt update \
    && apt install -y --no-install-recommends \
                      git \
                      apt-transport-https \
                      wget \
                      libpng-dev \
                      libonig-dev \
                      libxml2-dev \
                      zip \
                      openssl \
                      libzip-dev \
                      liblz4-dev \
                      libzstd-dev \
                      unzip \
                      libfreetype-dev \
                      libcurl4-openssl-dev \
                      pkg-config \
                      libssl-dev \
    && apt clean && rm -rf /var/lib/apt/lists/*

# Install PHP extensions
RUN    docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd fileinfo intl xdebug zip \
    && echo "xdebug.mode=debug" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && rm -rf /tmp/pear

# Enable Apache modules
RUN    apt install libapache2-mod-upload-progress \
    && a2enmod ssl headers rewrite && /etc/init.d/apache2 restart

# Get latest Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Change ownership of our application's files
RUN chown -R www-data:www-data /var/www/html

# Expose port 80 and start apache server
# No need to expose 9003, but I like to :o)
EXPOSE 80 9003
CMD ["apache2-foreground"]