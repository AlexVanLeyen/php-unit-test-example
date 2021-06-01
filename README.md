# PHP Unit Testing Example

This project demonstrates how to build and run unit tests with PHP.

## Dependencies:

- PHP-cli: 7.4
- PHPUnit: 9.5.4
- Docker: 19.03.11
- Docker-Compose: 1.26.0
- Composer: 2.0.14

## Services Available With Docker-Compose

- composer: package manager
- phpunit: unit testing framework
- php: runs the php cli

## Getting Started

```sh
git clone https://github.com/AlexVanLeyen/php-unit-test-example.git
cd php-unit-test-example
docker-compose run composer install
docker-compose run phpunit
```

After cloning the project onto your PC, enter the project's directory then install the dependencies for the project. Once the dependencies are installed, run phpunit to execute the sample tests in the project. You should see something like the following:

```
PHPUnit 9.5.4 by Sebastian Bergmann and contributors.

Runtime:       PHP 7.4.19
Configuration: /app/phpunit.xml

...                                                                 3 / 3 (100%)

Time: 00:00.006, Memory: 6.00 MB

OK (3 tests, 3 assertions)
```

## Composer

If you want to try adding additional packages to the project, run the following command:

```
docker-compose run composer require package-name
```

The composer docker container allows you to run composer without having to install all of its required dependencies.

For more commands, see https://getcomposer.org/doc/

**Note:** Anything added by the composer docker container will be owned by *root*. To prevent this, make sure to include the user and group id with the run command:
```sh
docker-compose run -u "$(id -u):$(id -g)" composer install
```

## PHP
If you want to try running php scripts directly, run the following command:
```sh
docker-compose run php replace-with-path-to-script.php
```

**Note:** you may need to grant the execution privilege to the script you want to run:
```sh
chmod 755 replace-with-path-to-script.php
```

## PHPUnit

See https://phpunit.readthedocs.io/en/9.5/textui.html#command-line-options or run `docker-compose run phpunit --help` to see all of the available options for phpunit. 

The configuration for PHPUnit is defined in `phpunit.xml`. Docs for configuration: https://phpunit.readthedocs.io/en/9.5/configuration.html

## Shortcuts
If the alias command is available to you, you can create a shortcut for your docker-compose commands:

```sh
alias dcr='docker-compose run -u "$(id -u):$(id -g)"
```

You should now be able to run something like this:
```sh
dcr composer --version
```

Adding `-u "$(id -u):$(id -g)"` to the alias is optional.