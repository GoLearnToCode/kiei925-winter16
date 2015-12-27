# Cheat Sheet: Model CRUD in the Rails Console

Models are our gateway to our application's data set.  Each model is a table of data.  We can have as many rows in the table as we want.  The columns are defined by the model's schema.

Once a model's table schema has been defined in the `db/models.yml` file and the corresponding `app/models` class file exists, we can create new rows to the table by having the user fill out forms in our web interface or by manually adding rows by using the `rails console` tool.  We can also read rows from the table, update individual rows, and delete rows.

These four activities --- create, read, update, and delete --- are often referred to by their acronum, `crud`.

This cheat sheet summarizes how to CRUD any given model using the Rails console.

For the purposes of this cheat sheet, we will presume that our `db/models.yml` file looks like this:

``` ruby
Book:
  title: string
  author: string
  summary: text
  hardcover: boolean
```

and that you've run the `rake db:migrate` command.  You should end up with a Book model class defined in `app/models/book.rb` that looks like this:

``` ruby
class Book < ActiveRecord::Base
end
```

and the `db/schema.rb` file should look something like this:

``` ruby
ActiveRecord::Schema.define(version: 20140402002437) do

  create_table "books", force: true do |t|
    t.string  "title"
    t.string  "author"
    t.text    "summary"
    t.boolean "hardcover"
  end

end
```

### Start the Rails Console

To begin, make sure you've started the console by opening a command prompt at your application folder:

```
rails console
```

You should see something like this:
```
Welcome to the Rails Console.
------------------------------------------------------------

Use this console to add, update, and delete rows from the database.

Models: Book

HINTS:
* Type 'exit' (or press Ctrl-D) to when you're done.
* Press Ctrl-C if things seem to get stuck.
* Use the up/down arrows to repeat commands.
* Type the name of a Model to see what columns it has.

Loading development environment (Rails 4.0.4)
irb(main):001:0>
```

**IMPORTANT**: Don't forget to read the HINTS section that's displayed for you!

### Creating New Rows

Adding new rows to a model's data table is pretty easy.  We just use the `.create` method on our model class, and provide a *hash* of data that assigns cell values for each column in our new row.

``` ruby
irb(main):001:0> Book.create(title: "Sherlock Holmes", author: "Arthur Conan Doyle")
   (0.1ms)  begin transaction
  SQL (0.4ms)  INSERT INTO "books" ("title") VALUES (?)  [["title", "Sherlock Holmes"]]
   (1.1ms)  commit transaction
=> #<Book {"id"=>3, "title"=>"Sherlock Holmes", "summary"=>nil, "author"=>"Arthur Conan Doyle", "hardcover"=>nil}>
```

There are some important things to notice in the above example:

* We don't have to provide values for every column.  If you don't provide a value for a `boolean` column, it will be assigned as `false`.  For all other column types, they will be `nil`.
* The INSERT jargon you see above is Ruby talking to the database on our behalf, instructing it to insert a new row into the table.
* The final line that starts with `=>` shows us the grand result of our `Book.create` instruction.  We've created a new `Book` object, and the database assigned it an `id` value of `3`.

### Reading Rows of Data

Reading, or *querying*, our model is also pretty easy.  There are lots of ways we to read data from the table, depending in what question you'd like to ask.

**How Many Rows Are There?**
`Book.count`

**Display All Rows**
`Book.all`

**What is the first book?**
`Book.first`

**What is the last book?**
`Book.last`

**Retrieve the book that has an `id` of 1.**
`Book.find_by(id: 1)`

**Retrieve all hardcover books.**
`Book.where(hardcover: true)`

**Retrieve the first book in the table that was written by Plato.**
`Book.find_by(author: "Plato")`
`Book.where(author: "Plato").first`

**How many paperback books are there?**
`Book.where(hardcover: false).count`

### Accessing a Row's Attributes

Once you have a row's worth of data in hand, you can drill down to a specific attribute.  To make things a little easier to follow in these examples, we show how to first capture the result of a query into a variable, then ask for a specific attribute.

**Who wrote 'Sherlock Holmes'?**

``` ruby
mystery_book = Book.find_by(title: "Sherlock Holmes")
mystery_book.author
```

**Is 'Sherlock Holmes' in paperback or hardcover?**

``` ruby
mystery_book = Book.find_by(title: "Sherlock Holmes")
mystery_book.hardcover?
=> false
```

### Updating a Row

Another thing you can do once you have retrieved a specific row is update it's attribute values.

``` ruby
mystery_book = Book.find_by(title: "Sherlock Holmes")
mystery_book.title = "The Adventures of Sherlock Holmes"
mystery_book.save
```

Notice that we have to call the `.save` method to update the data table based on the contents of our `mystery_book` variable.

### Deleting a Row

Finally, here's how we delete a row:

``` ruby
mystery_book = Book.find_by(title: "Sherlock Holmes")
mystery_book.delete
```

If you want to delete every row in the table in one fell swoop, you can. Here, we will ask for a before-and-after count to prove that we did indeed lose all of our data:

``` ruby
Book.count
=> 1

Book.delete_all
=> 1

Book.count
=> 0
```