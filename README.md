# WPFactory Autoloader
Autoload classes following WordPress naming conventions.

This will work as a default [PSR-4 autoloader](https://www.php-fig.org/psr/psr-4/) but with some differences:
- A `class-` will be prepended to the final class name
- Underscores in classes namespaces will be converted to dashes.
- Class names will always be converted to lowercase.

### Example ###
A class `TopLevelNamespace\My_Class` will call `class-my-class.php` file.

## Installation ##
Add this to your composer.json

```json
  "repositories": [
    {
      "type": "vcs",
      "url": "https://github.com/wpcodefactory/wpfactory-autoloader"
    }
  ],
  "require": {
    "wpfactory/wpfactory-autoloader":"dev-master"
  }
```

Don't forget to require the `autoload.php` to your project, as it's required for any composer library and to run `composer install`, of course :)

## Usage ##
You just need to instance the `WPFactory_Autoloader()` class passing two parameters to the `add_namespace()` method:
* The top-level namespace name of your your project, also known as a "vendor namespace"
* Base directory where the files are located

And then call the `init()` method.

### Example ###

```php
// Autoloader
$autoloader = new \WPFactory\WPFactory_Autoloader\WPFactory_Autoloader();
$autoloader->add_namespace( 'Your_Project_Namespace', plugin_dir_path( __FILE__ ) . '/src/php' );
$autoloader->init();
```
