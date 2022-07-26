FROM php:8.1-cli-alpine3.15

# git is required to allow Composer to work
RUN apk add --no-cache git libxslt-dev

RUN docker-php-ext-configure xsl \
    && docker-php-ext-install xsl

RUN git --version

RUN apk add --no-cache libzip-dev
RUN docker-php-ext-install zip

# install an old version otherwise “composer self-update” won't work
COPY --from=composer:2.3.9 /usr/bin/composer /usr/local/bin/composer

# install the public keys
RUN composer self-update

WORKDIR /symfony
