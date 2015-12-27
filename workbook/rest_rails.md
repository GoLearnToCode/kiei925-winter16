# Cheat Sheet: RESTful Routing in Rails

We know all about [RESTful routing](rest), but how do we actually implement it in Rails?

Consider a ```movies``` resource. We [already know how to do the following in the console](console_crud):

* (Read) List all the movies, or see the details for a single movie in the database
* (Create) Add a new movie to the database
* (Update) Change an existing movie in the database
* (Delete) Remove a movie from the database

It turns out that, in practice, there are exactly seven things we need to build so that a user can do this using your web application. Each of these seven things is called an *action*:

* An *index* action that lists all movies
* A *show* action that shows the details for one movie
* A *new* action that provides a form for creating a new movie
* A *create* action that actually creates the new movie based on user input
* An *edit* action that provides a form for editing an existing movie
* An *update* action that actually updates the movie based on user input
* A *destroy* action that deletes an existing movie

|Action  |HTTP Method/Verb|URL            |
|--------|----------------|---------------|
|index   |GET             |/movies        |
|show    |GET             |/movies/1      |
|new     |GET             |/movies/new    |
|create  |POST            |/movies        |
|edit    |GET             |/movies/1/edit |
|update  |PATCH           |/movies/1      |
|destroy |DELETE          |/movies/1      |

We can support all seven of these actions in our Rails application with just one line of code!

In ```routes.rb```,

```
resources :movies
```

Prove that it worked, by entering at the command prompt:

```
rake routes
```