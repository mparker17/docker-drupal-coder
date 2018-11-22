# Drupal coder Docker images

This repository has four images `phpcs-drupal`, `phpcbf-drupal`, `phpcs-drupalpractice`, and `phpcbf-drupalpractice`, for running Drupal coding linters.

They're designed to be run-able even if PHPCodeSniffer and/or the Coder module are not installed on your Drupal site. This is done by installing PHPCodeSniffer and the Coder module to `/opt/coder` inside the Docker image. This assumes that you mount your Drupal site's file system at `/app`

## Building

```
docker build -t phpcs-drupal ./phpcs-drupal/
docker build -t phpcbf-drupal ./phpcbf-drupal/
docker build -t phpcs-drupalpractice ./phpcs-drupalpractice/
docker build -t phpcbf-drupalpractice ./phpcbf-drupalpractice/
```

## Running

```
docker run --rm -v $PWD:/app phpcs-drupal $path_to_lint
docker run --rm -v $PWD:/app phpcbf-drupal $path_to_lint
docker run --rm -v $PWD:/app phpcs-drupalpractice $path_to_lint
docker run --rm -v $PWD:/app phpcbf-drupalpractice $path_to_lint
```
