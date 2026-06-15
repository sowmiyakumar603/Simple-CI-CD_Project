FROM php:8.2-apache

# Install system packages
RUN apt-get update && apt-get install -y \
    curl \
    git \
    unzip \
    gnupg \
    && rm -rf /var/lib/apt/lists/*

# Install Node.js 18
RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash - \
    && apt-get install -y nodejs

# Enable Apache rewrite
RUN a2enmod rewrite

# Set working directory
WORKDIR /var/www/html

# Copy frontend files
COPY . .

# Install npm dependencies
RUN npm install

# Install gulp CLI globally
RUN npm install -g gulp-cli

# Run gulp via package.json script
RUN npx gulp sass

# Permissions
RUN chown -R www-data:www-data /var/www/html

# Expose Apache port
EXPOSE 80

CMD ["apache2-foreground"]
