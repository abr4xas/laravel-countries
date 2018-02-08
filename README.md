<img align="left" width="180" src="https://blog.abr4xas.org/icons/apple-icon-180x180.png">

# Laravel Countries

[![Total Downloads](https://poser.pugx.org/abr4xas/laravel-countries/downloads.svg)](https://packagist.org/packages/abr4xas/laravel-countries)
[![Latest Stable Version](https://poser.pugx.org/abr4xas/laravel-countries/v/stable.svg)](https://packagist.org/packages/abr4xas/laravel-countries)
[![Latest Unstable Version](https://poser.pugx.org/abr4xas/laravel-countries/v/unstable.svg)](https://packagist.org/packages/abr4xas/laravel-countries)

Laravel Countries is a bundle for Laravel, providing Almost `ISO 3166_2`, `ISO 3166_3`, currency, Capital and more for all countries.

**Please note that version 1.4 is Laravel 5 only, older versions of Laravel should use version 1.3.4 instead**

---

## Installation

Add `abr4xas/laravel-countries` to `composer.json`.

    "abr4xas/laravel-countries": "dev-master"
    
Run `composer update` to pull down the latest version of Country List.

**If you're using Laravel 5.5, you don't have to edit `app/config/app.php`.**

Edit `app/config/app.php` and add the `provider` and `filter`

```php
'providers' => [
    Webpatser\Countries\CountriesServiceProvider::class,
]
```

Now add the alias.

```php
'aliases' => [
    'Countries' => Webpatser\Countries\CountriesServiceProvider::class,
]
```
    

## Model

You can start by publishing the configuration. This is an optional step, it contains the table name and does not need to be altered. If the default name `countries` suits you, leave it. Otherwise run the following command

```bash
$ php artisan vendor:publish --provider="Webpatser\Countries\CountriesServiceProvider"
```

Next generate the migration file:

```bash
$ php artisan countries:migration
$ composer dump-autoload
```
    
It will generate the `<timestamp>_setup_countries_table.php` migration and the `CountriesSeeder.php` seeder. To make sure the data is seeded insert the following code in the `seeds/DatabaseSeeder.php`

```php
//Seed the countries
$this->call('CountriesTableSeeder');
$this->command->info('Seeded the countries!'); 
```

You may now run it with the artisan migrate command:

```bash
$ php artisan migrate --seed
```

After running this command the filled countries table will be available
