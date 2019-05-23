# Add custom image size

Add to `platform/themes/your-theme/functions/functions.php` or in your plugin service providers.

```php
if (!function_exists('register_custom_image_size')) {
    function register_custom_image_size()
    {
        config([
            'media.sizes.post-small'   => '200x150',
            'media.sizes.post-featured' => '360x217', // You can add more sizes if you want
        ]);
    }
}
add_action('init', 'register_custom_image_size', 1234);
```

How to use:

```php
    {{ get_image_url($post->image, 'post-small') }}
    {{ get_object_image($post->image, 'post-small') }}
```