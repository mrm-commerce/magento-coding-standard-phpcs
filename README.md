# MRM Commerce Magento 2 Coding Standard

## Description
A package consisting of two PHP Code Sniffer rulesets meant to ensure or increase the code quality of Magento 2 projects.
### Ruleset #1: MrmCommerceMagento2CodingStandard
The core ruleset of this coding standard. It consists of rules from several other coding standards like:
- The Magento 2 Coding Standard - the official one and all rules from it are automatically included here
- PSR-12 - set of rules from the PHP Standards Recommendation #12 which expanded and replaced the PSR-2 coding
  style guide
- PHP Compatibility Coding Standard - for checking the code for incompatibilities with the selected PHP version
- Security Audit Coding Standard - for issues related with security like possible SQL injections or insecure functions
  usage
- Slevomat Coding Standard - advanced and configurable coding standard providing a lot of functional, cleaning
  and formatting sniffs that aim to make the code more consistent, safer and easier to read and maintain

### Ruleset #2: MrmCommerceMagento2CodingStandardSafeMode
The Safe Mode version of the coding standard makes PHP Code Sniffer report the same issues as the ruleset described above.
However, it has a few more rules that apply only to the PHP Code Beautifier and Fixer (phpcbf) in order to minimize the
risk of applying automatic fixes that could break your code, like enforcing strict types or adding type hints. 

The Safe Mode is designed to help with bulk updates. You can use it to improve the quality of your entire project with
just a single CLI command without having to double-check every single file to determine if something got broken.

For everyday use it's recommended to use the non-safe version of the coding standard for improving files you currently
work on and to double-check what exactly got changed.

## Installation instructions
1. Ensure that other dependencies of your project don't conflict with 
   dependencies - e.g. if your project requires `"dealerdirect/phpcodesniffer-composer-installer": "^0.5"`, 
   you can remove it (`composer remove dealerdirect/phpcodesniffer-composer-installer` or a direct removal from 
   `composer.json`) as this package will install a newer version
2. Run the following command: `composer require mrm-commerce/magento-coding-standard-phpcs --dev`
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
or using the safe mode
```
php vendor/bin/phpcs --standard=vendor/mrm-commerce/magento-coding-standard-phpcs/MrmCommerceMagento2CodingStandardSafeMode/ruleset.xml vendor/your-vendor/
```
Both the regular ruleset and the safe mode ruleset will report the same issues but in case of the safe mode less issue
types are marked as being able to be fixed automatically. 
As an optional parameter you can include `--runtime-set testVersion X.Y` (e.g. `--runtime-set testVersion 7.1`) to
specify the PHP version the check should be run against in order to get the most of the PHP Compatibility Coding 
Standard:
```
php vendor/bin/phpcs --runtime-set testVersion 7.1 --standard=vendor/mrm-commerce/magento-coding-standard-phpcs/MrmCommerceMagento2CodingStandard/ruleset.xml vendor/your-vendor/
```

## FAQ
### PHPCBF automatically adds syntax that's not compatible with my PHP version
Ensure that you are running PHPCBF/PHPCS using the same PHP version that's used in your project. Some sniffs will detect your PHP version and will react accordingly. 

