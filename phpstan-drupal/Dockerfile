FROM composer:1.8.5
WORKDIR /opt/phpstan
RUN composer require 'mglaman/phpstan-drupal:0.11.7'
WORKDIR /app
VOLUME /app
ENTRYPOINT ["/opt/phpstan/vendor/bin/phpstan" "analyse" "-c /opt/phpstan/vendor/mglaman/phpstan-drupal/extension.neon"]
