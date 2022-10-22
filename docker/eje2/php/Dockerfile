FROM php:7.2-fpm-alpine
RUN apk add --no-cache postgresql-dev \
	&& docker-php-ext-install pdo pdo_pgsql 
EXPOSE 9000