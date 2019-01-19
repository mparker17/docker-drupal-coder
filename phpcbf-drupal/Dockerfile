FROM composer:1.8.0
WORKDIR /opt/coder
RUN composer require 'drupal/coder:8.3.1'
RUN /opt/coder/vendor/bin/phpcs --config-set installed_paths /opt/coder/vendor/drupal/coder/coder_sniffer
WORKDIR /app
VOLUME /app
ENTRYPOINT ["/opt/coder/vendor/bin/phpcbf", "--standard=Drupal"]
