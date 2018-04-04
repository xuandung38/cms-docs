# Upgrade Guide

- [Upgrade To 3.0](#upgrade-3.0)
- [Upgrade To 2.6](#upgrade-2.6)
- [Upgrade To 2.4.1](#upgrade-2.4.1)
- [Upgrade To 2.4](#upgrade-2.4)
- [Upgrade To 2.3](#upgrade-2.3)
- [Upgrade To 2.2.1](#upgrade-2.2.1)
- [Upgrade To 2.2](#upgrade-2.2)
- [Upgrading To 2.1](#upgrade-2.1)

<a name="upgrade-3.0"></a>
## Upgrade from 2.6 to 3.0

- Copy your theme to new source code.
- Run `composer install` to update vendor packages.
- Run `php artisan migrate` to update database.

> {warning} Old custom plugin which you built with Botble CMS v2.6 will not work on v3.0.

<a name="upgrade-2.5"></a>
## Upgrade from 2.5 to 2.6
- Run `composer install` to update vendor packages.
- Run `php artisan migrate` to update database.

<a name="upgrade-2.4.1"></a>
## Upgrade from 2.4 to 2.4.1
- Run `composer install` to update vendor packages.
- Run `php artisan plugin:activate member`

<a name="upgrade-2.4"></a>
## Upgrade To 2.4
- Copy what you changes (plugins, themes) and paste to new version 2.4.
- Route `public.single.detail` change to `public.single`.
- Should use new database from /database.sql. Old database can not be used.

<a name="upgrade-2.3"></a>
## Upgrade To 2.3

> {warning} You should not upgrade to version 2.3 if your project is stable now. Because it has a lot of change so it can break your site.

- Override folder `/core` and `/plugins` from new version.

- Replace `public/vendor` folder or run `php artisan vendor:publish --tag=assets`

- Check and update manually 3 files: `composer.json`, `gulpfile.js`, `.env`

- Because we created new media management and changed database so you have to re-upload all your files.

- Replace `get_file_by_size()` by `get_image_url()`


<a name="upgrade-2.2.1"></a>
## Upgrade To 2.2.1

Remove admin bar configuration in your theme

    class="{{ admin_bar_class() }}"
    {!! admin_bar() !!}
    
Remove admin breadcrumb in your plugin if it is exists.

    {!! Breadcrumbs::render('pageTitle', trans('download::category.create'), Route::currentRouteName()) !!}
    <div class="clearfix"></div>

<a name="upgrade-2.2"></a>
## Upgrade To 2.2

Remove this line on `/config/app.php`
    
    Lord\Laroute\LarouteServiceProvider::class,
    
Remove laroute on `composer.json`
    
    "lord/laroute": "~2.4",

There are many changes on `gulpfile.js` so if you don't change anything on this file. Please replace it with new `gulpfile.js`.

Then, if you are using `Linux` or `OSX`, you can use `upgrade.sh` to continue upgrade to version 2.2.

    $ sudo chmod -R 777 upgrade.sh
    $ ./upgrade.sh

Upgrade script for Windows OS will be update soon. From now, you can follow `upgrade.sh` content to upgrade your source code.

<a name="upgrade-2.1"></a>
## Upgrading To 2.1

> {warning} This version using Laravel Framework 5.4 so if you are working on Laravel 5.3, please override all default files and folders of Laravel version 5.4 before upgrade.

### Core and plugins
Override folder `/core` and `/plugins` from new version.

### Public resource
Replace `public/vendor` folder.

### Check and update manually
- composer.json
- gulpfile.js
- .env
