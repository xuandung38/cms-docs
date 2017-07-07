# Introduction
- [Requirement](#requirement)
- [Installation](#installation)
- [Note](#note)

<a name="requirement"></a>
## Requirement


- Apache, nginx, or another compatible web server.
- PHP >= 5.6.4 >> Higher
- MySQL Database server
- OpenSSL PHP Extension
- Mbstring PHP Extension
- Exif PHP Extension
- Fileinfo Extension
- Module Re_write server
- PHP_CURL Module Enable


> {note} On this projects, I use the latest Laravel version (currently 5.4). Please go to [Laravel documentation page](https://laravel.com/docs) for more information.

<a name="installation"></a>
## Installation

### Manual installation

**- Import sample database from `database/dump/base.sql`**

**- Create `.env` file from `.env-example` and update your configuration**

**- Open CMD and run `composer install` or `composer update` to install vendor packages.**

**- Run your website in the browser**: `php artisan serve`

### Install using shell script
* Chmod 777 for `install.sh`
* Run file `./install.sh`

> {tip} For Linux users
    
    If you got this error /usr/bin/env: ‘bash\r’: No such file or directory"
    Please run `sed $'s/\r$//' ./install.sh > ./install.Unix.sh` 
    and use ./install.Unix.sh to install
    If you got this error "bash: ./install.sh: Permission denied"
    Please run `sudo chmod 777 -R install.sh` to make sure this file has permission to execute

<a name="note"></a>
## Note

This site can only be run at domain name, not folder link.

On your localhost, setting virtual host. Something like `http://cms.local` is ok.

Cannot use as `http://localhost/cms/...`.

Please remove `public` in your domain also, you can point your domain to `public` folder

or use `.httaccess` (http://stackoverflow.com/questions/23837933/how-can-i-remove-public-index-php-in-the-url-generated-laravel)

Follow these steps to see how to config virtual host: [Setup virtual host](/v/2.1/virtualhost).

Well done! Now, you can login to the dashboard by access to your_domain_site/admin.

    Username: botble
    Password: 159357

Enjoy!