# Due Thursday, April 23, 11:59pm

### Final project application setup

In your ```code``` directory, create the Rails application for your final project using ```rails new final```. This will create a new folder called ```final``` in your ```code``` directory – add this folder to Github.

Add the following line to your ```Gemfile```:

```gem 'ez'```

Then, from your command prompt – Terminal (Mac) or Command Prompt with Ruby on Rails (Windows) – issue the following command from within your ```code/final``` directory:

```bundle install```

Complete the following requirements for a total possible score of 10 points:

1. (5 points) Add a ```models.yml``` file to your application's ```db``` directory. Begin building your application's domain model by adding at least three models. Run ```rake db:migrate``` from the command prompt to build your application's model classes.
2. Modify the ```db/seeds.rb``` file and load your database with data. When you run ```rake db:seed``` it should:
  * (1 point) Wipe the database clean 
  * (2 points) Create at least 5 records per model
  * (2 points) Create at least 1 relationship between models