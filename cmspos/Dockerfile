# Use PHP 8.1 with Apache
FROM php:8.1-apache

# Install system dependencies
RUN apt-get update && apt-get install -y \
    libzip-dev \
    zip \
    unzip \
    && docker-php-ext-install pdo pdo_mysql zip

# Enable Apache modules
RUN a2enmod rewrite && a2enmod headers

# Copy Apache configuration
COPY apache.conf /etc/apache2/sites-available/000-default.conf
RUN a2ensite 000-default

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Set working directory
WORKDIR /var/www/html

# Copy PHP configuration
COPY php.ini /usr/local/etc/php/conf.d/custom.ini

# Copy composer files first for better caching
COPY extensions/composer.json extensions/composer.lock* extensions/

# Install PHP dependencies
RUN cd extensions && composer install --no-dev --optimize-autoloader

# Copy application code
COPY . .

# Set permissions
RUN chown -R www-data:www-data /var/www/html

# Expose port 80
EXPOSE 80

# Start Apache
CMD ["apache2-foreground"]