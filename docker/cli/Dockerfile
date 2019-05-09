FROM amazeeio/php:7.2-cli-drupal

COPY composer.json composer.lock /app/
RUN composer install --no-dev
COPY . /app

# Generate OAuth keys.
RUN openssl genrsa -out /app/keys/private.key 2048
RUN openssl rsa -in /app/keys/private.key -pubout > /app/keys/public.key
RUN chmod 660 /app/keys/*.key

# Set permissions.
RUN chmod 555 /app/web/sites/default
RUN chmod 440 /app/web/sites/default/settings.php
RUN chmod 775 /app/web/sites/default/files

# Define where the Drupal Root is located
ENV WEBROOT=web
