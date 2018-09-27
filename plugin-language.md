# Language

## Apply multi language for your new plugin

- Open `/plugins/<your-plugin>/src/Providers/<YourPlugin>ServiceProvider.php`. Add below code to function `boot`

```php
$this->app->booted(function () {
    if (defined('LANGUAGE_MODULE_SCREEN_NAME')) {
        config(['plugins.language.general.supported' => array_merge(config('plugins.language.general.supported'), [<YOUR_PLUGIN>_MODULE_SCREEN_NAME])]);
    }
});
```
