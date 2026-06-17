FROM php:8.2-apache

RUN apt-get update && apt-get install -y \
    curl \
    git \
    unzip \
    gnupg \
    && rm -rf /var/lib/apt/lists/*

RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash - \
    && apt-get install -y nodejs

RUN a2enmod rewrite

WORKDIR /var/www/html

COPY . .

WORKDIR /var/www/html/frontend

RUN npm install
RUN npm install -g gulp-cli
RUN npx gulp sass

RUN chown -R www-data:www-data /var/www/html

EXPOSE 80

CMD ["apache2-foreground"]
