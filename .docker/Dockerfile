FROM php:8.1-cli-alpine3.15

COPY --from=composer:2 /usr/bin/composer /usr/local/bin/composer

# git is required to allow Composer to work
RUN apk add --no-cache git libxslt-dev
#RUN apk add --no-cache libxslt-dev

RUN docker-php-ext-configure xsl \
    && docker-php-ext-install xsl

RUN git --version

WORKDIR /symfony
