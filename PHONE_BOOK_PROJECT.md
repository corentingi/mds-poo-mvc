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


## MySQL version

If using MySQL version 5.7 or earlier, you will need to update your `/app/Providers/AppServiceProvider.php` to contain:

```php
use Illuminate\Support\Facades\Schema;

/**
 * Bootstrap any application services.
 *
 * @return void
 */
public function boot()
{
    Schema::defaultStringLength(191);
}
```

Source: [StackOverflow](https://stackoverflow.com/questions/42244541/laravel-migration-error-syntax-error-or-access-violation-1071-specified-key-wa)


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


### Exercise 2: Configure database

Create a new database `phone_book` and configure the connection to it in your Laravel application.

To configure the database, modify the file `.env` to see the following lines:
```ini
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=phone_book
DB_USERNAME=root
DB_PASSWORD=root
```

If the `.env` file is not in your project, create it at the root of your project.

You can use PhpMyAdmin to create the database `phone_book`.


### Exercise 3: Create the contacts table

We want to create a new table `contacts` that we will use to store contact information.

You could create this table manually, but Laravel allows you to automate this action with [database migrations](https://laravel.com/docs/10.x/migrations).

You can use `artisan` to create and manipulate database migrations :
- `php artisan make:migration create_contacts_table`
- `php artisan migrate`
- `php artisan migrate:fresh`

Steps:
- Create the table using migrations with the following columns:
  - first_name
  - last_name
  - date_of_birth
  - phone_number
  - email


### Exercise 4: Contact model

We will create a new model called `Contact` associated with the table `contacts` in our database.

Laravel automatically links the `Contact` model with the table named `contacts`.

You can create the contact with the following command:
- `php artisan make:model Contact`

There is no need to define properties in our model, because Laravel will automatically make the columns available to us.


### Exercice 5: List contacts

We now want to display the contacts available in our database.

Note: You can add some contacts manually in our table with PhPMyAdmin.

Steps:
- Create a controller `ContactController` using `artisan`
- Ensure the Controller knows how to use the model `Contact`: `use App\Models\Contact;`
- Create a new view `contact.list` using `artisan`

You can add manually some contacts in database to display them.


### Exercice 6: Create contacts

Now that we have the list of contacts. We want to be able to add contacts from the application.

- Create a form that will ask for contact information.
- Implement the right method in `ContactController` to save a new contact in database.
- Add a route that will serve the newly implemented method from the controller.
- After the contact is inserted in database, redirect to the list of contacts.


### Exercices 7: Delete contacts

Add a button to delete contacts from the list.
After a delete, redirect the user to the contact list.


### Exercice 8: Contact details

Create a page that displays more information about the contact.

Example:
- When I go to the page `/contacts/154` I should see the contact page of the contact number 154 in my database.

You can add some more columns in the database. For example:
- address
- photo
- etc...

### Exercice 9: Contact groups

Create a new table `Groups`.

This table will store groups names, for example `MyDigitalSchool students`.

Create a relationship between `Contacts` and `Groups`.

Use the Laravel docs: [Eloquent relationships](https://laravel.com/docs/10.x/eloquent-relationships)

You can create groups manually in your database and associate them with contacts on when creating them.

### Exercice 10: Edit existing contact details

Create a new page with a form that allows to modify an existing contact and saving them with a save button.
