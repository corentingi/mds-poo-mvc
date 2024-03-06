# Phone book project with Laravel

## Setup

Check if you have php and composer installed.
You can run this in a terminal (Powershell / Bash on windows)
```bash
php --version
# PHP 8.1.11 (cli) (built: Sep 29 2022 20:02:53) (NTS)
# Copyright (c) The PHP Group
# Zend Engine v4.1.11, Copyright (c) Zend Technologies
#     with Zend OPcache v8.1.11, Copyright (c), by Zend Technologies

composer --version
# Composer version 2.4.3 2022-10-14 16:56:41
```

If not, you need to install both:
1) PHP: https://www.php.net/manual/en/install.php
2) Composer: https://getcomposer.org/


## Laravel

Laravel is a PHP framework that implements the MVC architecture pattern.

See details on the page: [Laravel](LARAVEL.md)

To implement the basic features with Laravel you will need to work in the following folders:
- Routes: `routes/web.php`
- Models: `app/Models`
- Views: `resources/views`
- Controllers: `app/Http/Controllers`

You can follow a course online (English) about Laravel:
- https://laracasts.com/series/laravel-8-from-scratch


**Note:** `artisan` is a php script installed with Laravel that will allow you to simplify a lot of actions.

You can use `artisan` to test features of php and Laravel in an interractive terminal: `php artisan tinker`

## VS Code

If you are using VS Code, you can install the following extensions:
- PHP Intelliphense
- Laravel Extra Intellisense

Optional:
- Laravel Blade Snippets


## Exercises

After each exercise, remember to commit your work before moving to the next.
This will allow you to reset your work to a known state if you need to.


### Exercise 0: Setting up Laravel

Steps:
- Open a terminal
- Create a new Laravel project if it is not done already: `composer create-project ...` (see the page [Laravel](LARAVEL.md))
- Open the project in VS Code (The new proejct has been created in a new folder)
- Commit your work with an "Initial commit"


### Exercise 1: Landing page

In this exercise, we will first understand how Laravel works to display a simple landing page.

Steps:
- Go to `routes/web.php` to check the existing routes
- Modify the existing route for `/` to display a new view `home`
- Create a new view in `resources/views/home.blade.php` (You can make a simple HTML page)
  - You can use `php artisan make:view` to create the view.

You can implement this using only `Routes` and `Views`.


### Exercise 2: Contact model

Create a new model that will be our `Contact` model.

The `Contact` model should have some properties:
- first_name
- last_name
- date_of_birth
- phone_number
- email

You can create the contact with the following command:
- `php artisan make:model`
- Specify the name of the model: `Contact`
- Tick the line "Migration" (move with arrows and toggle with space bar)
- press enter

The migration was created in `./database/migrations`.


### Exercise 3: Configure database

Create a new database `phone_book` and configure the connection to it in your Laravel application.

To configure the database, create a file `.env` and add the following lines:
```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=phone_book
DB_USERNAME=root
DB_PASSWORD=root
```

You can use PhpMyAdmin to create the database `phone_book`.


### Exercise 4: Fill in the migration

You can use `artisan` and the `migrations` to update the database automatically.

If you created your model with a migration, you can modify the migration and run it to update the database.

You should read the documentation here: https://laravel.com/docs/10.x/migrations

The following commands are usefull:
- `php artisan migrate`
- `php artisan migrate:fresh`


### Exercice 5: Display contacts

We now want to display the list of contacts.
- Create a controller `ContactController` using `artisan`
- Link the Controller to the model `Contact`
- Create a new view `contact.blade.php` using `artisan`

You can add manually some contacts in database to display them.
