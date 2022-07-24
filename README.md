# MRM Commerce Magento 2 Coding Standard

## MrmCommerceMagento2CodingStandard Ruleset Description
MrmCommerceMagento2CodingStandard is the core ruleset of this coding standard. It consists of rules from several other 
coding standards like:
- The Magento 2 Coding Standard - the official one, all rules from it are automatically included here
- PSR-12 - set of rules from the PHP Standards Recommendation #12 which expanded and replaced the PSR-2 coding
  style guide
- PHP Compatibility Coding Standard - for checking the code for incompatibilities with the selected PHP version
- Security Audit Coding Standard - for issues related with security like possible SQL injections or insecure functions
  usage
- Slevomat Coding Standard - advanced and configurable coding standard providing a lot of functional, cleaning
  and formatting sniffs that aim to make the code more consistent, safer and easier to read and maintain
The ruleset is designed to prevent phpcbf (PHP Code Beautifier and Fixer) from automatic fixes to reported errors and
warnings that may make your code to stop working. This means that you can use phpcbf to perform bulk fixes of the code
in your custom modules instead of fixing every single issue manually. Just remember to always check the result before 
committing or merging it.

## Installation instructions
1. Ensure that other dependencies of your project don't conflict with 
   dependencies - e.g. if your project requires `"dealerdirect/phpcodesniffer-composer-installer": "^0.5"`, 
   you can remove it (`composer remove dealerdirect/phpcodesniffer-composer-installer` or a direct removal from 
   `composer.json`) as this package will install a newer version
2. Run the following command: `composer require mrm-commerce/magento-coding-standard-phpcs --dev --with-dependencies`
3. You should see the package and its dependencies being installed with the following information at the 
   end of the output:
   ```PHP CodeSniffer Config installed_paths set to ../../magento/magento-coding-standard,../../mrm-commerce/magento-coding-standard-phpcs,../../mrm-commerce/phpcs-security-audit,../../phpcompatibility/php-compatibility,../../slevomat/coding-standard```
4. If you see the `Failed to set PHP CodeSniffer installed_paths Config` error instead of the output above or you do not
   see any output related to phpcs at all, you can run the following commands manually from your Magento root directory:
   ```
   cd vendor/squizlabs/php_codesniffer/
   php ./bin/phpcs --config-set installed_paths ../../magento/magento-coding-standard,../../mrm-commerce/magento-coding-standard-phpcs,../../mrm-commerce/phpcs-security-audit,../../phpcompatibility/php-compatibility,../../slevomat/coding-standard
   ```

## Usage
Once the package is installed, you can use it to check your code using the following command:
```
php vendor/bin/phpcs --standard=vendor/mrm-commerce/magento-coding-standard-phpcs/MrmCommerceMagento2CodingStandard/ruleset.xml vendor/your-vendor/
```
As an optional parameter you can include `--runtime-set testVersion X.Y` (e.g. `--runtime-set testVersion 7.4`) to
specify the PHP version the check should be run against in order to get the most of the PHP Compatibility Coding 
Standard:
```
php vendor/bin/phpcs --runtime-set testVersion 7.4 --standard=vendor/mrm-commerce/magento-coding-standard-phpcs/MrmCommerceMagento2CodingStandard/ruleset.xml vendor/your-vendor/
```

## FAQ
### PHPCS suggests changes that are not compatible with the PHP version I'm using on my project
Ensure that you are running PHPCS using the same PHP version that's used in your project.
For example, if a remote server hosting your Magento website runs PHP 7.3, you should not use 7.4 locally.
Some sniffs will detect your PHP version and will react accordingly. Be aware that the PHP version that you defined
in project settings will be ignored and the actual PHP version you run your project on will be used.

### PHPCBF automatically adds syntax that's not compatible with my PHP version
Ensure that you are running PHPCBF/PHPCS using the same PHP version that's used in your project. Some sniffs will detect your PHP version and will react accordingly. 

