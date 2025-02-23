# ./docker/frontend/Dockerfile.dev
# Can use other images but, I am using this to save up some time
FROM php:8.3-apache

# Install Node.js and npm
RUN curl -sL https://deb.nodesource.com/setup_22.x | bash -

# Install system dependencies
RUN    apt-get update \
    && apt-get install -y --no-install-recommends \
        git \
        apt-transport-https \
        wget \
        zip \
        openssl \
        unzip \
        nodejs \
    && apt-get clean && rm -rf /var/lib/apt/lists/*
    
RUN corepack enable && yes "y" | yarn exec env

# Enable Apache modules
RUN a2enmod headers rewrite && /etc/init.d/apache2 restart

# Set working directory
WORKDIR /var/www/html

# Install global npm packages
RUN yarn global add @angular/cli@17.3.8

# Expose port 80 and 5173 (vite dev port)
EXPOSE 80 5173

# Start Apache
CMD ["apache2-foreground"]