# MRM Commerce Magento 2 Coding Standard

## Description
A package of two PHP Code Sniffer rules meant to ensure or increase the code quality of Magento 2 projects.

## Installation instructions
1. Ensure that other dependencies of your project don't conflict with 
   dependencies - e.g. if your project requires `"dealerdirect/phpcodesniffer-composer-installer": "^0.5"`, 
   you can remove it (`composer remove dealerdirect/phpcodesniffer-composer-installer` or a direct removal from 
   `composer.json`) as this package will install a newer version
2. Run the following command: `composer require mrm-commerce/magento-coding-standard-phpcs --dev`
3. You should see the package and its dependencies being installed with the following information at the 
   end of the output:
   ```PHP CodeSniffer Config installed_paths set to ../../magento/magento-coding-standard,../../mrm-commerce/magento-coding-standard-phpcs,../../mrm-commerce/phpcs-security-audit,../../phpcompatibility/php-compatibility,../../slevomat/coding-standard```
4. If you see the `Failed to set PHP CodeSniffer installed_paths Config` error instead of the output above, 
   you can run the following commands manually from your Magento root directory:
   ```
   cd vendor/squizlabs/php_codesniffer/
   php ./bin/phpcs --config-set installed_paths ../../magento/magento-coding-standard,../../mrm-commerce/magento-coding-standard-phpcs,../../mrm-commerce/phpcs-security-audit,../../phpcompatibility/php-compatibility,../../slevomat/coding-standard
   ```


## FAQ
### PHPCBF automatically adds syntax that's not compatible with my PHP version
Ensure that you are running PHPCBF/PHPCS using the same PHP version that's used in your project. Some sniffs will detect your PHP version and will react accordingly. 

