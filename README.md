# MRM Commerce Magento 2 Coding Standard

## Description
A set of PHP Code Sniffer rules meant to ensure or increase the code quality of Magento 2 projects.

## Installation instructions
1. Ensure that other dependencies of your project don't conflict with dependencies - e.g. if your project require `"dealerdirect/phpcodesniffer-composer-installer": "^0.7.1"`, you can remove it (`composer remove dealerdirect/phpcodesniffer-composer-installer` or a direct removal from `composer.json`) as this package will install a newer version
2. Run the following command: `composer require mrm-commerce/magento-coding-standard`

## FAQ
### PHPCBF automatically adds syntax that's not compatible with my PHP version
Ensure that you are running PHPCBF/PHPCS using the same PHP version that's used in your project. Some sniffs will detect your PHP version and will react accordingly. 

