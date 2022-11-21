FROM composer as vendor
COPY /src /app
RUN composer install --ignore-platform-reqs

FROM craftcms/php-fpm:8.0 

USER root
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin/ --filename=composer
USER www-data

COPY --chown=www-data:www-data ./src /app
COPY --chown=www-data:www-data --from=vendor /app/vendor /app/vendor
RUN composer update
