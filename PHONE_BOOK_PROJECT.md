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
- Create a local git repository: `git init` (On windows you might need to run `git config core.autocrlf false` if you have issues with `git add .`)
- Commit your work with an "Initial commit"


### Exercise 1: Landing page

In this exercise, we will first understand how Laravel works to display a simple landing page.

Steps:
- Go to `routes/web.php` to check the existing routes
- Modify the existing route for `/` to display a new view `home`
- Create a new view in `resources/views/home.blade.php` (You can make a simple HTML page)

You can implement this using `Routes` only.


### Exercise 2: Contact table

Setup a contact table in the database using using Laravel models and migrations.
