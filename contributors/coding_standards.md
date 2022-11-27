## Coding standards and tests

PHP Code Sniffer is available via composer, the standard used is defined in phpcs.xml.diff:
````bash
composer phpcs
````

PHPStan is configured at level 8, you can check for errors locally using:
`````bash
composer phpstan
`````

PHPUnit is available, you can check for errors locally using:
`````bash
composer phpunit
`````

If you want you can call all three validators bu using this:
`````bash
composer phpall
`````


## Tools

## Composer commands

* `composer phpcs`: Apply the coding standards
* `composer phpstan`: Scans codebase and looks for both obvious & tricky bugs
* `composer phpunit`: Runs unit tests suite
* `composer rector`: Refactor the codebase with Rector
* `composer phpall`: Runs all previous commands
* `vendor/bin/phpstan analyse --generate-baseline`: If you want to regenerate a PHPStan baseline run this command:
