FROM composer as vendor
COPY /src /app
RUN composer install --ignore-platform-reqs

FROM craftcms/php-fpm:8.0 

COPY --chown=www-data:www-data ./src /app
COPY --chown=www-data:www-data --from=vendor /app/vendor /app/vendor

WORKDIR /app/web
CMD [ "php", "-S", "0.0.0.0:80" ]