# Page template

## Create new layout template
- Create a layout file in `/public/themes/<current theme>/layouts` following `default.blade.php` in this folder. Then customize it like you want.

Example: `custom-layout.blade.php`
```php
{!! Theme::partial('header') !!}
{!! Theme::content() !!}
{!! Theme::partial('footer') !!}
```

- Register new template to `/public/themes/<current theme>/functions/functions.php`

```php
register_page_template([
    'custom-layout' => __('Custom layout'), // custom-layout is the name of layout file.
]);
```

- Go to Admin panel -> Pages and select template `Custom layout` for a page to test.