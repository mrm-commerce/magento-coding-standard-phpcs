# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.2.0] - 2020-07-22
### Changed
- Some data in composer.json (the ruleset itself remained unaffected)

## [1.1.2] - 2020-07-05
### Added
- One exclusion a rule that disallows exception naming which is a convention in Magento:
SlevomatCodingStandard.Classes.SuperfluousExceptionNaming.SuperfluousSuffix

## [1.1.1] - 2020-05-14
### Added
- One exclusion a rule that would just throw a lot of warnings for constructors:
SlevomatCodingStandard.Classes.ParentCallSpacing.IncorrectLinesCountBeforeControlStructure
- Basic description in the readme file

## [1.1.0] - 2020-05-10
### Added
- This changelog along with all the updates for previous versions
- Inclusion of Slevomat, PHPCompatibility and PSR12 rulesets by default
- A lot of exclusions for Slevomat rules we don't want to use and for one
PSR2 rule
- Configuration for some Slevomat rules to adjust them to how things are
done in Optaros

### Changed
- The required version of Slevomat coding standard has been changed in order
to keep new rules from being included before they're reviewed

### Removed
- Consistence coding standard - turned out to be obsolete

## [1.0.1] - 2020-04-07
### Added
- More dependencies: Consistence coding standard, Slevomat coding standard
and PHPCompatibility coding standard. In order to keep the experimental
branch's dependencies in sync with the latest release

## [1.0.0] - 2020-03-23
### Added
- Initial set of dependencies: M2 coding standard, Pheromone security audit
Code Sniffer and dealerdirect's Composer Installer
- A ruleset including all rules from the M2 coding standard and the security
audit rulesets
