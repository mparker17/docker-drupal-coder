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

# Other tools

[The dockerized-php project](https://github.com/dockerized-php) provides some code-quality-analysis tools that are not directly related to Drupal but are still pretty useful:

* [bmitch/churn-php](https://packagist.org/packages/bmitch/churn-php) identifies php files that could be good candidates for refactoring based on how many git commits they have and their cyclomatic complexity. Run with:

        docker run --rm -v $PWD:/app dockerizedphp/churn run $path_to_lint

* [infection/infection](https://packagist.org/packages/infection/infection) measures the effectiveness of a test set in terms of its ability to detect faults. Run with:

        docker run --rm -v $PWD:/app dockerizedphp/infection run $path_to_lint

* [psecio/iniscan](https://packagist.org/packages/psecio/iniscan) scans a PHP.ini file to determine if it follows security best practices. Run with:

        docker run --rm -v /path/to/php.ini:/tmp dockerizedphp/iniscan scan --path=php.ini

* [phploc/phploc](https://packagist.org/packages/phploc/phploc) ("PHP lines of code") measures the comment+non-comment+logical lines of code in a set of PHP files, and analyzes their cyclomatic complexity, dependencies between them, and how they're structured, and provides a summary. Run with:

        docker run --rm -v $PWD:/app dockerizedphp/phploc $path_to_lint

* [povils/phpmnd](https://packagist.org/packages/povils/phpmnd) ("PHP magic number detector") detects numeric and string literals that could change at a later stage, and would otherwise be hard to update unless they are turned into constants. Run with:

        docker run --rm -v $PWD:/app dockerizedphp/phpmnd $path_to_lint

* [phpmd/phpmd](https://packagist.org/packages/phpmd/phpmd) ("PHP mess detector") detects clean code problems, code size problems, design problems, naming problems, and unused code. Run with:

        docker run --rm -v $PWD:/app dockerizedphp/phpmd $path_to_lint text cleancode,codesize
