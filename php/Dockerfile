FROM php:8.1-fpm

RUN apt update \
    && apt install -y zlib1g-dev g++ git libicu-dev zip libzip-dev zip \
    && docker-php-ext-install intl opcache pdo pdo_mysql \
    && pecl install apcu \
    && docker-php-ext-enable apcu \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip

WORKDIR /var/www/symfony_docker

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN curl -sS https://get.symfony.com/cli/installer | bash \
    && ls -la /root/.symfony/bin/ \
    && mv /root/.symfony/bin/symfony /usr/local/bin/symfony || echo "Symfony CLI not found!"

RUN git config --global user.email "patryk180885@gmail.com" \
    && git config --global user.name "Zuku101"
