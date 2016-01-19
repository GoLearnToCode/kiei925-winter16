# Due Sunday, 11:59pm

### Final project application setup

Begin work on what will ultimately become your final project. Create a new workspace, cloning it from https://github.com/kiei925-winter16/rails-template

Then, from your command prompt, issue the following command:

```bundle install```

Complete the following requirements for a total possible score of 10 points:

1. (5 points) Add a ```models.yml``` file to your application's ```db``` directory. Begin building your application's domain model by adding at least three models. Run ```rake db:migrate``` from the command prompt to build your application's model classes.
2. Modify the ```db/seeds.rb``` file and load your database with data. When you run ```rake db:seed``` it should:
  * (1 point) Wipe the database clean 
  * (2 points) Create at least 5 records per model
  * (2 points) Create at least 1 relationship between models
