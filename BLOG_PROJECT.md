# Blog project with Laravel

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
2) Composer: https://getcomposer.org/download/


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


### Exercise 2: Blog posts
In this exercise we will try to create a really simple blog.

We want to have a page that lists all our posts:
- `http://localhost/posts`

A post can look like this:
```html
<h1>My first blog post</h1>

<p>
    Anim irure mollit qui id veniam et ut dolor Lorem mollit ut. Minim velit est anim esse nulla proident non consectetur officia. In Lorem est amet labore commodo laboris veniam reprehenderit ullamco labore elit. Consectetur reprehenderit culpa minim qui cupidatat irure ut fugiat velit reprehenderit incididunt sit ad anim.
</p>
```

You can implement this using `Routes` and `Views` only.


### Exercise 3: Store blog posts in HTML files

We now have a page `http://localhost/posts` that is able to display all our blog posts.

However we would like to have a single page per blog posts to make easier to add more and more posts.

We want to have a single dynamic route that will display the post given in the URL:
- `http://localhost/posts/my-first-post`

The blog posts will be stored on the disk, in a folder that we will create: `resources/posts/`:
- `resources/posts/my-first-post.html`
- `resources/posts/my-second-post.html`
- `resources/posts/my-third-post.html`

The `http://localhost/posts` should link to those pages.

When the blog post doesn't exist, you can return a 404 error to the browser.

You can implement this using `Routes` and `Views` only.


### Exercise 4: Use a model to provide the blog posts

In this exercise, we will improve the existing blog mechanism by creating a **model** `Post` that will find the post files for us.

Steps:
- You can create a `Post` class in a file called `app/Models/Post.php`
- Implement a static method `Post::find($post)` that will return the content of the post
- Modify the existing route `http://localhost/posts/my-first-post` to use this `Post` model

You can use `artisan` to create the model: `php artisan make:model Post`

You can implement this using `Routes`, `Models` and `Views` only.


### Exercise 5: Use the created model to list all posts

In this exercise, we will improve the existing blog mechanism by using the **model** `Post` to list all our posts on the `http://localhost/posts` page.

Steps:
- You can create a static method `Post::list()` that will list the posts from the disk
- Modify the existing route `http://localhost/posts` to use this `Post` model

To be able to list the files on disk, you can use the `File` facade from Laravel: `use Illuminate\Support\Facades\File;`

You can implement this using `Routes`, `Models` and `Views` only.


### Exercise 6: Use YAML front matter to improve the list of all posts

In this exercise, we will improve the list of posts by using a metadata in our blog posts files (`my-first-post.html`).

This metadata is call [YAML front matter](https://github.com/spatie/yaml-front-matter).

Steps:
- Import the package using composer
- Add metadata to all our blog posts
- Improve the existing `http://localhost/posts` using the package to display post `Titles, Date, Author, Extract`

You can implement this using `Routes`, `Models` and `Views` only.


### Exercise 7: Use a controller to manage posts

In this exercise, we will group all the actions that can happen on our posts inside a Controller.

Steps:
- Create a controller for the posts: `PostController`
- Implement a method `list($post)` to handle listing our posts
- Implement a method `show()` to handle showing a single post
- Modify the existing routes to use the `PostController`

You can use `artisan` to create the controller: `php artisan make:controller PostController`


### Going further

So far we have stored articles locally and we are only able to write them in a text editor.

To make the application more dynamic, we could add some features:
- A category to each post and a way to display them on a page for each category
- A search bar to filter the articles
- A Database to store our posts instead of using files
- A Form that allows creating new posts
