<img align="left" width="180" src="https://blog.abr4xas.org/icons/apple-icon-180x180.png">

## Laravel Countries

[![Latest Stable Version](https://poser.pugx.org/abr4xas/laravel-countries/v/stable?format=flat-square)](https://packagist.org/packages/abr4xas/laravel-countries)
[![Total Downloads](https://poser.pugx.org/abr4xas/laravel-countries/downloads?format=flat-square)](https://packagist.org/packages/abr4xas/laravel-countries)
[![Latest Unstable Version](https://poser.pugx.org/abr4xas/laravel-countries/v/unstable?format=flat-square)](https://packagist.org/packages/abr4xas/laravel-countries)
[![License](https://poser.pugx.org/abr4xas/laravel-countries/license?format=flat-square)](https://packagist.org/packages/abr4xas/laravel-countries)
[![composer.lock](https://poser.pugx.org/abr4xas/laravel-countries/composerlock?format=flat-square)](https://packagist.org/packages/abr4xas/laravel-countries)

Laravel Countries is a bundle for Laravel, providing Almost `ISO 3166_2`, `ISO 3166_3`, currency, Capital and more for all countries.

---

### Installation

Add `abr4xas/laravel-countries` to `composer.json`.

```json
"abr4xas/laravel-countries": "dev-master"
```

Run `composer update` to pull down the latest version of Country List.

> In Laravel 5.5, with Package Auto Discovery it should all be set automatically. For < 5.5, follow these instructions after composer finishes package installation:

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

### Model

You can start by publishing the configuration. This is an optional step, it contains the table name and does not need to be altered. If the default name `countries` suits you, leave it. Otherwise run the following command

```bash
$ php artisan vendor:publish --provider="Webpatser\Countries\CountriesServiceProvider"
```

Next generate the migration file:

```bash
$ php artisan countries:migration
```

It will generate the `<timestamp>_setup_countries_table.php` migration and the `CountriesTableSeeder.php` seeder. To make sure the data is seeded insert the following code in the `seeds/DatabaseSeeder.php`

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
