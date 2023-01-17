# School book project with Laravel

Let's create a school book using Laravel

## Laravel

You can find a lot of resource about Laravel online. Here are a few interesting reads:
- Laravel docs and getting started: https://laravel.com/docs/9.x
- Laravel API: https://laravel.com/api/5.8/index.html


## Project

We want to create a simple school book with phone numbers.

Goals:
- Understanding the MVC architecture pattern
- Understanding how Object Oriented Programming can be used in an MVC project

### Database

The database `school_book` we will be using contains the following tables:
- `students`: This table contains a list of students
  - `id`
  - `gender`
  - `given_name`
  - `family_name`
  - `streetaddress`
  - `city`
  - `zipcode`
  - `email`
  - `phone`
  - `birthday`
- `school_classes`: This table contains a list of classes
  - `id`
  - `class`: Seconde, Première, Terminale
  - `number`: A, B, C, D, E
  - `year`: 2015, 2016, 2017

There is a table used to link both tables together: `school_class_student`


### Models

The base application already contains one Model to be used with the database: `Student`

During this project you will have to create models for the other tables in our database.


## Exercises

### Exercise 0: Setup

Let's first setup the base of the project

1) Check that you have `php` and `composer` installed:
    - `php --version`
    - `composer --version`
2) Fork the project on GitHub: https://github.com/corentingi/poo-mvc-exercise-school-book
3) Clone the **forked** project locally: `git clone git@github.com:your-github-username/poo-mvc-exercise-school-book.git`
4) Configure the project: Create a `.env` file containing the correct information to connect to the database
5) Install dependencies: `composer install`
6) Start a development server with artisan `php artisan serve`
7) Check that everything works by loading the main page: http://localhost:8000 (You should see a page with a list of students)

**Note:** For this part we will be using the database `catalog`


#### Exercise 1: Student list

**Objective**
Create a page to display a list of students and some basic information.

This page should list only a few students at the start (~20 students)

**Steps:**
- Create the controller `StudentController`
- Create a method `list()` in the controller to handle the action
- Make the route `/students` use this controller function
- Design a simple page to display the student list

**Commit all your changes to Git**


#### Exercise 2: Add a pagination to the list of students

**Objective**
To explore more than the first 20 students, we need a way to handle pages.

**Steps:**
- Add the query parameter `page` to select the page to display
- Modify the query to get the right page: https://laravel.com/docs/9.x/pagination#main-content
- Check that this is working loading the page: `http://localhost:8000/students?page=1`
- Add a simple selector to go the next and previous pages

**Commit all your changes to Git**


#### Exercise 3: Order students on their age

**Objective**
Add an ordering feature using query parameters

We should be able to order the list of students by `birthday`:
- `/students?order_by=birthday&order=asc`

**Commit all your changes to Git**


#### Exercise 4: Student information page

**Objective**
Create a page for each student to display its information.
All information about the user should be displayed.

**Steps:**
- Create a method `show($student_id)` in the controller `StudentController` to handle the action
- Make the route `/students/{student_id}` use this controller function
- Design a simple page to display the student information

**Commit all your changes to Git**


#### Exercise 5: Display the classes of a student

**Objective**
On the student information page, we want to list all the classes they have been in:
- `2015: Seconde A`
- `2016: Première B`
- `2017: Terminale C`

**Steps:**
- Add the necessary code in the view to display this information

**Commit all your changes to Git**


#### Exercise 6: Class list

**Objective**
Create a page to display a list of classes and some basic information:
- Name of the class
- Year
- Number of students

This page can list all classes or have a pagination mechanism (BONUS).

**Steps:**
- Create the controller `SchoolClassController`
- Create a method `list()` in the controller to handle the action
- Make the route `/classes` use this controller function
- Design a simple page to display the class list

**Commit all your changes to Git**


#### Exercise 7: Class detail page

**Objective**
Create a page for each class to display its information.
This page should contain a list of all the students in the class.

**Steps:**
- Create a method `show($class_id)` in the controller `SchoolClassController` to handle the action
- Make the route `/classes/{class_id}` use this controller function
- Design a simple page to display the class information and the list of students in the class

**Commit all your changes to Git**


#### Exercise 8: Clean up

**Objective**
Have a look in all the functions and pages created to ensure everything works.
You can add links between pages to make navigation easier.

**Commit all your changes to Git**
