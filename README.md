# QubusPHP Coding Standards

Coding standard rulesets for QubusPHP.

QubusPHP coding standards loosely follows the [Laminas Coding Style Guide](https://docs.laminas.dev/laminas-coding-standard/) with a few exceptions:

1. Abstract classes MUST NOT be prefixed/suffixed with `Abstract`.
2. Traits MUST NOT be prefixed/suffixed with `Trait`.
3. Interfaces MUST NOT be prefixed/suffixed with `Interface` or `Contract`.
4. Exceptions MUST be suffixed with `Exception`.
5. File name of classes must be in PascalCase.
6. File names of functions must be in lowercase and can be delimited with `_`.
7. Custom functions must be namespaced and imported when used.
8. Classes must be coded to interfaces and follow SOLID.

## Installation

1. Install the coding standard as a dependency of your project:

```bash
$ composer require --dev qubus/qubus-coding-standard
```

2. Add coding standard to the PHP_CodeSniffer install path:

```bash
 vendor/bin/phpcs --config-set installed_paths vendor/qubus/qubus-coding-standard
```

3. Run the standards:

```bash
 vendor/bin/phpcs /path/to/code
```