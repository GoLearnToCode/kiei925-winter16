# Cheat Sheet: Sorting and Limiting Data

Once we know the basics of creating, reading, updating, and deleting rows of model data, we can move on to more advanced scenarious.  This cheat sheet answers two questions in particular:

1. Now that we know how to retrieve rows of data with the `.read` method, how do we sort that data for display purposes?
1. What do we do when we have a thousand rows in our table, but we only want to display the first ten?  

For the purposes of this cheat sheet, we will presume that our `db/models.yml` file looks like this:

``` ruby
Book:
  title: string
  author: string
  hardcover: boolean
  rating: integer   # 1 to 5 stars
```

and that you've run the `rake db:migrate` command.  You should end up with a Book model class defined in `app/models/book.rb` that looks like this:

``` ruby
class Book < ActiveRecord::Base
end
```

and we're going to presume that we have some data in our database already:

| id |title|author|hardcover|rating|
|----|-----|------|---------|------|
|1|The Lord Of The Rings|J.R.R. Tolkien|true|5|
|2|A Brief History of Time|Stephen Hawking|true|3|
|3|Alice in Wonderland|Lewis Carroll|false|4|
|4|The Hobbit|J.R.R. Tolkien|false|4|


### How To Sort Data

We use the `.order` method to sort data by any column by appending it to our `.read` statement:

``` ruby
Book.order("title")
```

| id |title|author|hardcover|rating|
|----|-----|------|---------|------|
|2|A Brief History of Time|Stephen Hawking|true|3|
|3|Alice in Wonderland|Lewis Carroll|false|4|
|4|The Hobbit|J.R.R. Tolkien|false|4|
|1|The Lord Of The Rings|J.R.R. Tolkien|true|5|


By default, the data will be sorted in ascending order.  We can explicitly specify the sort direction, by specifying either `asc` or `desc`:

``` ruby
Book.order("title desc")
```

| id |title|author|hardcover|rating|
|----|-----|------|---------|-------|
|1|The Lord Of The Rings|J.R.R. Tolkien|true|5|
|4|The Hobbit|J.R.R. Tolkien|false|4|
|3|Alice in Wonderland|Lewis Carroll|false|4|
|2|A Brief History of Time|Stephen Hawking|true|3|

### How to Limit the Number of Rows

We can use the `.limit` method:

``` ruby
Book.limit(2)
```

| id |title|author|hardcover|rating|
|----|-----|------|---------|-------|
|1|The Lord Of The Rings|J.R.R. Tolkien|true|5|
|2|A Brief History of Time|Stephen Hawking|true|3|


### Putting It All Together

All of the paperbacks sorted alphabetically by author:

``` ruby
Book.where(hardcover: false).order("author asc")
```

| id |title|author|hardcover|rating|
|----|-----|------|---------|-------|
|3|Alice in Wonderland|Lewis Carroll|false|4|
|4|The Hobbit|J.R.R. Tolkien|false|4|

The two highest-rated books:

``` ruby
Book.order("rating desc").limit(2)
```

| id |title|author|hardcover|rating|
|----|-----|------|---------|-------|
|1|The Lord Of The Rings|J.R.R. Tolkien|true|5|
|3|Alice in Wonderland|Lewis Carroll|false|4|
