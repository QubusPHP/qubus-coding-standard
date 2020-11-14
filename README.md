# QubusPHP Coding Standards

Coding standard rulesets for QubusPHP components and the framework.

QubusPHP coding standards loosely follows the [Laminas Coding Style Guide](https://docs.laminas.dev/laminas-coding-standard/) with a few exceptions:

1. Abstract classes MUST NOT be prefix/suffixed with `Abstract`.
2. Traits MUST NOT be prefixed/suffixed with `Trait`.
3. Interfaces MUST NOT be prefixed/suffixed with `Interface` or `Contract`.
4. Exeptions MUST be suffixed with `Exception`.
5. File name of classes must be in PascalCase.
6. File names of functions must be in lowercase.
7. Custom functions must be namespaced and imported when used.
8. Classes must be coded to interfaces and follow SOLID.

## Installation

1. Install the module via composer by running:

   ```bash
   $ composer require qubus/coding-standard
   ```

2. Add composer scripts into your `composer.json`:

   ```json
   "scripts": {
     "cs-check": "phpcs",
     "cs-fix": "phpcbf"
   }
   ```

3. Create file `phpcs.xml` on base path of your repository with this content:

   ```xml
   <?xml version="1.0"?>
   <ruleset xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xsi:noNamespaceSchemaLocation="vendor/squizlabs/php_codesniffer/phpcs.xsd">
   
       <arg name="basepath" value="."/>
       <arg name="cache" value=".phpcs-cache"/>
       <arg name="colors"/>
       <arg name="extensions" value="php"/>
       <arg name="parallel" value="80"/>
       
       <!-- Show progress -->
       <arg value="p"/>
   
       <!-- Paths to check -->
       <file>config</file>
       <file>src</file>
       <file>test</file>
   
       <!-- Include all rules from the QubusPHP Coding Standard -->
       <rule ref="QubusPHPCodingStandard"/>
   </ruleset>
   ```