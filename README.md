# QubusPHP Coding Standards

Coding standard rulesets for QubusPHP components and the framework.

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

1. Install the module via composer by running:

```bash
$ composer require laminas/laminas-coding-standard
```

2. Add composer scripts into your `composer.json`:

```json
"scripts": {
   "cs-check": "phpcs",
   "cs-fix": "phpcbf"
}
```

3. Create file `phpcs.xml` on base path of your repository with the following content:

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
   <file>tests</file>

   <!-- Additional QubusPHP Coding Standard rules. -->

   <!-- File names should be lowercased and class names should be uppercase. -->
   <rule ref="Generic.Files.LowercasedFilename">
      <exclude name="Generic.Files.LowercasedFilename.NotFound"/>
   </rule>
   <rule ref="SlevomatCodingStandard.Files.TypeNameMatchesFileName">
      <exclude name="SlevomatCodingStandard.Files.TypeNameMatchesFileName.NoMatchBetweenTypeNameAndFileName"/>
   </rule>

   <!-- A cast statement MUST NOT be preceeded by a single space. -->
   <rule ref="Generic.Formatting.SpaceBeforeCast">
      <exclude name="Generic.Formatting.SpaceBeforeCast.NoSpace"/>
   </rule>

   <!-- The Short array syntax MUST be used-->
   <rule ref="Generic.Arrays.DisallowShortArraySyntax">
      <exclude name="Generic.Arrays.DisallowShortArraySyntax.Found"/>
   </rule>

   <!-- Opening brace must be on a new line. -->
   <rule ref="Generic.Classes.OpeningBraceSameLine">
      <exclude name="Generic.Classes.OpeningBraceSameLine.BraceOnNewLine"/>
   </rule>

   <!-- Opening brace should be on a new line after declaration. -->
   <rule ref="Generic.Functions.OpeningFunctionBraceKernighanRitchie">
      <exclude name="Generic.Functions.OpeningFunctionBraceKernighanRitchie.BraceOnNewLine"/>
   </rule>

   <!-- Constants true, false and null MUST be lowercase. -->
   <rule ref="Generic.PHP.UpperCaseConstant">
      <exclude name="Generic.PHP.UpperCaseConstant.Found"/>
   </rule>
   <rule ref="Generic.PHP.LowerCaseConstant"/>

   <!-- There MUST be at least one space on either side of an equals sign used
      to assign a value to a variable. In case of a block of related
      assignments, more spaces MUST NOT be inserted before the equal sign. -->
   <rule ref="Generic.Formatting.MultipleStatementAlignment">
      <exclude name="Generic.Formatting.MultipleStatementAlignment.NotSame"/>
      <properties>
         <property name="error" value="true"/>
         <property name="maxPadding" value="50"/>
      </properties>
   </rule>

   <!-- Code MUST use an indent of 4 spaces for each indent level, and MUST
      NOT use tabs for indenting. If tabs are use, indent with 4 spaces. -->
   <rule ref="Generic.WhiteSpace.ScopeIndent">
      <properties>
         <property name="indent" value="4"/>
         <property name="exact" value="true"/>
         <property name="tabIndent" value="true"/>
         <property name="--tab-width" value="4"/>
      </properties>
   </rule>
   <rule ref="Generic.WhiteSpace.DisallowSpaceIndent">
      <exclude name="Generic.WhiteSpace.DisallowSpaceIndent.SpacesUsed"/>
   </rule>

   <!-- Abstract classes MUST NOT have an `Abstract` prefix/suffix. -->
   <rule ref="WebimpressCodingStandard.NamingConventions.AbstractClass">
      <exclude name="WebimpressCodingStandard.NamingConventions.AbstractClass"/>
   </rule>
   <rule ref="SlevomatCodingStandard.Classes.SuperfluousAbstractClassNaming"/>

   <!-- Exception classes MUST have an `Exception` suffix. -->
   <rule ref="WebimpressCodingStandard.NamingConventions.Exception"/>
   <rule ref="SlevomatCodingStandard.Classes.SuperfluousExceptionNaming">
      <exclude name="SlevomatCodingStandard.Classes.SuperfluousExceptionNaming.SuperfluousSuffix"/>
   </rule>

   <!-- Interface classes MUST NOT have an `Interface` prefix/suffix. -->
   <rule ref="SlevomatCodingStandard.Classes.SuperfluousInterfaceNaming"/>

   <!-- Trait classes MUST NOT have a `Trait` suffix. -->
   <rule ref="SlevomatCodingStandard.Classes.SuperfluousTraitNaming"/>

   <!-- The Yoda comparison CAN be used. -->
   <rule ref="SlevomatCodingStandard.ControlStructures.DisallowYodaComparison">
      <exclude name="SlevomatCodingStandard.ControlStructures.DisallowYodaComparison.DisallowedYodaComparison"/>
   </rule>

   <!-- File names should be lowercased and class names should be uppercase. -->
   <rule ref="Generic.Files.LowercasedFilename">
      <exclude name="Generic.Files.LowercasedFilename.NotFound"/>
   </rule>
   <rule ref="SlevomatCodingStandard.Files.TypeNameMatchesFileName">
      <exclude name="SlevomatCodingStandard.Files.TypeNameMatchesFileName.NoMatchBetweenTypeNameAndFileName"/>
   </rule>

   <!-- Include the rest of the rules from the Laminas Coding Standard -->
   <rule ref="LaminasCodingStandard"/>
</ruleset>
```
4. In the above, make sure to change the `Paths to check` to paths that should be checked in your project.