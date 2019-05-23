# Drupal coder Docker images

This repository has several Docker images for Drupal code quality analysis...

* `eslint-es5-drupal` which runs Drupal's ECMAScript 5 coding standards lints,
* `eslint-es6-drupal` which runs Drupal's ECMAScript 6 coding standards lints,
* `phpcs-drupal` which runs Drupal's coding standards lints,
* `phpcs-drupalpractice` which runs Drupal's best practices lints,

... and several Docker images to automatically fix code quality issues...

* `phpcbf-drupal` which automatically fixes code to conform to Drupal's coding standards,
* `phpcbf-drupalpractice` which automatically fixes code to conform to Drupal's best practices.

These Docker images are designed to be run-able even if eslint and/or PHPCodeSniffer and/or the Coder module are not installed on your Drupal site. This is done by installing eslint and/or PHPCodeSniffer and the lints into `/opt` inside the Docker image. This assumes that you mount your Drupal site's file system at `/app`. They're ideal for use with Lando, Docksal, etc.

## Building

```
docker build -t eslint-es5-drupal ./eslint-es5-drupal/
docker build -t eslint-es6-drupal ./eslint-es6-drupal/
docker build -t phpcs-drupal ./phpcs-drupal/
docker build -t phpcbf-drupal ./phpcbf-drupal/
docker build -t phpcs-drupalpractice ./phpcs-drupalpractice/
docker build -t phpcbf-drupalpractice ./phpcbf-drupalpractice/
```

## Running

```
docker run --rm -v $PWD:/app eslint-es5-drupal $path_to_lint
docker run --rm -v $PWD:/app eslint-es6-drupal $path_to_lint
docker run --rm -v $PWD:/app phpcs-drupal $path_to_lint
docker run --rm -v $PWD:/app phpcbf-drupal $path_to_lint
docker run --rm -v $PWD:/app phpcs-drupalpractice $path_to_lint
docker run --rm -v $PWD:/app phpcbf-drupalpractice $path_to_lint
```
