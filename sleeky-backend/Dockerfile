FROM php:8.0-apache

RUN apt-get update && apt-get install -y \
    curl \
    git \
    unzip \
    python3 \
    make \
    g++ \
    nodejs \
    npm \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /var/www/html

COPY . .

RUN npm install

EXPOSE 80
