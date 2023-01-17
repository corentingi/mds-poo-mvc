# Movie catalog project with Laravel

Let's create a movie catalog using Laravel

## Laravel

You can find a lot of resource about Laravel online. Here are a few interesting reads:
- Laravel docs and getting started: https://laravel.com/docs/9.x
- Laravel API: https://laravel.com/api/5.8/index.html


## Project

We want to design an online catalog for Movies and TV Series.

Goals:
- Understanding the MVC architecture pattern
- Understanding how Object Oriented Programming can be used in an MVC project

### Database

The database we will be using contains the following tables:
- `movies`: This table contains a list of movies that we have in the catalog
- `series`: This table contains a list of series that we have in the catalog
- `episodes`: This table contains a list of episodes for each series that we have in the catalog
- `genres`: This table contains a list of genres
- There are other tables to put in place relationships between those tables: `movies_genres`, `series_genres`, `episodes_genres`

Those tables contain basic information to display to the user: `title, year, runtime, plot, poster image, ratings, etc.`


### Models

The base application already contains one Model to be used with the database: `Movie`

During this project you will have to create models for the other tables in our database.


## Exercises

### Part 1

#### Exercise 0: Setup

Let's first setup the base of the project

1) Fork the project on GitHub: https://github.com/corentingi/mds-poo-exercice-catalog
2) Clone the project locally: `git clone git@github.com:xxxx/mds-poo-exercice-catalog.git`
3) Configure the project: Create a `.env` file containing the correct information to connect to the database
4) Install dependencies: `composer install`
5) Start a development server with artisan `php artisan serve`
6) Check that everything works by loading the main page: http://localhost:8000 (You should see a page with a list of movies)

**Note:** For this part we will be using the database `catalog`


#### Exercise 1: Movie page

**Objective**
Create a page to display a movie and all it's information.

**Steps:**
- Create the controller `MovieController`
- Create a method `show($id)` in the controller to handle the action
- Add the route `/movies/{id}`
- Design a simple page to display the movie information

**Commit all your changes to Git**

#### Exercise 2: Page to list all movies

**Objective**
Create a page that lists the first 20 movies found in database.

**Steps:**
- Create a method `list()` in the `MovieController` to handle the action
- Add the route `/movies`
- Design a simple page to display the movie list

This page should contain the list of movies with their title, poster and basic information.

**Commit all your changes to Git**


#### Exercise 3: Add a pagination feature to the list of movies

**Objective**
To explore more than the first 20 movies, we need a way to handle pages.

**Steps:**
- Add the query parameter `page` to select the page to display
- Modify the query to get the right page
- Check that this is working loading the page: `http://localhost:8000/movies?page=1`
- Add a simple selector to go the next and previous pages

**Commit all your changes to Git**


#### Exercise 4: Add an ordering parameter

**Objective**
Add an ordering feature using query parameters

We should be able to order the list of movies by `startYear` and `averageRating`:
- `/movies?order_by=startYear&order=asc`
- `/movies?order_by=averageRating&order=desc`

**Commit all your changes to Git**


#### Exercise 5: Display a movie at random

**Objective**
We want to provide a pages that can return a movie at random.
This should help users find new stuff to watch.

**Steps:**
- Add a new route `/movie/random`
- Add a new function in the `MovieController` to handle this action
- Re-use the existing view to display the page

**BONUS:**
- Display a random movie on the front page too

**Commit all your changes to Git**


#### Exercise 6: List available movie genres

**Objective**
Add a page to list all available movie genres.

**Steps:**
- Add the model `Genre`
- Add the controller `GenreController`
- Add a function `list` to the controller
- Add the page `/genres` to return the list of genres available

**Commit all your changes to Git**


#### Exercise 7: List movies of a specific genre

**Objective**
Add a filter to list only movies of a specific genre.

**Steps:**
- Add the required code to handle a relationship between `Movies` and `Genre`: https://laravel.com/docs/9.x/eloquent-relationships
- Change the `MovieController` to handle this filter: `/movies?genre=Action`
- Add links to move from the page `/genres` to `/movies?genre=Action`

**Commit all your changes to Git**


#### Exercise 8: Add support for TV series too

**Objective**
For the moment we can only manage movies in our catalog.
We also have TV series and their episodes in the database and would like to also support TV series.

TV series are a bit different, there is the series itself and each episode have their own information.

**Steps:**
- Add a new models to manage the TV series and episodes: `Series`, `Episode`
- Add the relationship between the two: https://laravel.com/docs/9.x/eloquent-relationships
- Create a new controller `SeriesController` to be used later.

Note: `Series` is special as it always has an `s` at the end, even as singular.

**Commit all your changes to Git**


#### Exercise 9: List TV series

**Objective**
Now that we have the controller and relationship ready, create the page to list the series in the database.

**Steps:**
- Add a new controller function `list()` to handle this action
- Add a new route `/series` (to list all TV series)
- Add filters the same way they work for movies

You can re-use the work done for listing movies with filters and pagination.

**Commit all your changes to Git**


#### Exercise 10: Show a TV series details

**Objective**
A TV series has information of itself that we can display.
When we click on a series in the list, we want to display its details.


**Steps:**
- Add a new controller function `show()` to handle this action
- Add a new route `/series/{id}` (to display a single series information)
- Add a new view to display a series information
- Add links between the pages: `/series` and `/series/{id}`

**BONUS:**
- Also add the `/series/random` page to find a random series

**Commit all your changes to Git**


#### Exercise 11: List a TV series episodes

**Objective**
A TV series is a bit special as it contains multiple episodes.
We want to list those episodes in the series page `/series/{id}`, but also add a new page for the details of each episodes.

**Steps:**
- Add new routes:
  - `/series/{id}/season/{season_num}`: List all episode of a given season
  - `/series/{id}/season/{season_num}/episode/{episode_num}`: Show information about a specific episode
- Add new controller functions to handle those actions
- Add new view to display the pages

**Commit all your changes to Git**


#### Exercise 12: Search bar

**Objective**
We would like to be able to search from the main page through all the movie, series and episodes available.
When using the search bar, the results should be displayed on a separate page with the link to those movies, series, episodes.

You can start by searching only movies and then add TV series and episodes in a second time.

Note: the results page can have the following route: `/search?q=my search`

**Commit all your changes to Git**



### Part 2: Refactoring

Our database engineers have realized that having 3 tables (`Movies`, `Series` and `Episodes`) was making things difficult.
They have decided to change the way we store them and have a single database called `Title` which will contain all type of medias.

**Note:** For this part we will be using the database `catalog_v2`


#### Exercise 1: Refactor the application

**Objective**
Change the code of the application to handle the new table `Title`


**Hints:**
- Add a new model `Title`
- The models `Movie`, `Series` and `Episode` could now inherit from this `Title` class
- The controllers `MovieController`, `SeriesController` and `EpisodeController` could inherit from a `TitleController`
- We can now factorize most functions:
  - Some Controller functions can be factorized
  - The search function can be improved now that all results derive from the same Model

**Commit all your changes to Git**
