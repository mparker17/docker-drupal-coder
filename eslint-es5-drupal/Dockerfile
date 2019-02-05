FROM node:10.15
WORKDIR /opt/drupal
RUN curl -o 'package.json' -L 'https://cgit.drupalcode.org/drupal/plain/core/package.json?h=8.7.x&id=b332b27928582f39365e6ab0e738a511578c9115' && \
  npm install && \
  curl -o '.eslintrc.legacy.json' -L 'https://cgit.drupalcode.org/drupal/plain/core/.eslintrc.legacy.json?h=8.7.x&id=b332b27928582f39365e6ab0e738a511578c9115'
WORKDIR /app
VOLUME /app
ENTRYPOINT ["/opt/drupal/node_modules/.bin/eslint", "-c", "/opt/drupal/.eslintrc.legacy.json"]
