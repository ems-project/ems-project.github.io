# Coding standards and tests

## Coding standards

We will not define an exhaustive list of coding standards.
However PHP Code Sniffer is available via composer, the standard used is defined in phpcs.xml.diff:
````bash
composer phpcs
````

## Code quality

PHPStan is configured at level 8, you can check for errors locally using:
`````bash
composer phpstan
`````

In order to run at level 8 for every subproject, we generated a baseline for some exceptions that we are not able to handle properly.
However, it is forbidden to add any new exceptions without a very good reason.

If you really need to regenerate a PHPStan baseline run this command:

`````bash
vendor/bin/phpstan analyse --generate-baseline
`````
## Tests

PHPUnit is available, you can check for errors locally using:

`````bash
composer phpunit
`````

## Best practices

Rector is also available in order to ensure that PHP and Symfony best practices are followed. The standards to follows are defined in the [`rector.php`](https://github.com/ems-project/elasticms/blob/4.x/rector.php) config file. 

`````bash
composer rector
`````

## Run all validators

If you want you can call all those previous validators byu using this composer's shortcut:

`````bash
composer phpall
`````

## Exceptions

When there is an unexpected exception, an exception that should never happened, like an exception throw in order to solve a phpstan issue, throw a ```\RuntimeException```. We should avoid using ```\Exception``` in order to simplify logs analysis.

In other cases you should or use a specific exception, which can be handled upper in the stack. Or throw a [Symfony HTTP based exception](https://github.com/symfony/http-kernel/tree/5.x/Exception):

- 401: Symfony\Component\HttpKernel\Exception\UnauthorizedHttpException
- 404: Symfony\Component\HttpKernel\Exception\NotFoundHttpException
- 405: Symfony\Component\HttpKernel\Exception\MethodNotAllowedHttpException