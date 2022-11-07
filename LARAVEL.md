# Laravel

Laravel is a PHP framework that implements the MVC architecture pattern.

## Creating a new Laravel project

You can create a Laravel project using the following command:
```bash
composer create-project laravel/laravel mds-poo-mvc-exercise

```

Composer will create a new project using the `laravel/laravel` template.  
This will create the project in a new directory `mds-poo-mvc-exercise`.  

Move into the new create project directory:
```bash
cd mds-poo-mvc-exercise
```

## Using Artisan

After the Laravel project is created, you will be able to use a php script installed with your Laravel project and called `artisan`.
This script provides a lot of command to manage your Laravel project.

**Start a local dev web server**
```bash
php artisan serve
```

**Create a models, controlers, others**
```bash
php artisan make:model Post
php artisan make:controller PostController
...
```

**Test features of php and Laravel functions in an interractive terminal**
```bash
php artisan tinker
```

## MVC with Laravel

To implement the basic features with Laravel you will need to work in the following folders:
- Routes: `routes/web.php`
- Models: `app/Models`
- Views: `resources/views`
- Controllers: `app/Http/Controllers`


You can follow an online course (English) about the basic features of Laravel:
- https://laracasts.com/series/laravel-8-from-scratch
