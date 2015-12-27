# Cheat Sheet: Ruby Data Containers, Part 2: Hashes

There are two primary _data containers_ that Ruby provides out-of-the-box for us when we need to manage a list of things: Arrays and Hashes.

This cheat sheet will focus on how to manage a simple list using a hash.

Find a Rails application that you've created, start the `rails console` and follow along.

### Creating a List using a Hash

A hash maintains a list similar to an array, but has a different use-case in mind.  We use a hash instead of an array when we want to retrieve elements from the list, but don't know the order.  Recall that when we use arrays, we need to know the zero-based index of an element in order to retrieve it.  Often, that's an inconvenient requirement when we're managing data.

A hash lets us retrieve arbitrary elements by associating each element with a **key**. A key is a label or indicator of some kind.  Usually we use Ruby **symbols** as keys for the elements in the hash.  This relieves us from knowing __a priori__ the element order.  Instead, if we know the key for our element, we can retrieve it.

Say we need to manage the data for a movie [Apollo 13](http://www.imdb.com/title/tt0112384).  How can we keep track of the most important attributes of the movie, such as the title, year of publication, and average review ating?

```ruby
movie = { title: 'Apollo 13', year: 1995, rating: 7.6 }
```

Here we create a variable named `movie` that will hold our movie data.  We use the curly braces `{ }` to tell Ruby that we want to use a `Hash` to hold our list of attributes.

A hash ties a set of labels to their associated values, and will allow us to access individual values by asking for their label (usually called the **key**).  We use the colon `:` to connect each key to a particular value.

### How Many Elements?

We can determine the number of elements inside a hash by using any of the following methods:

```ruby
movie.count
movie.size
movie.length
```

These are all synonyms for each other.  Use whichever one feels most natural.

### Retrieving Individual Values

Suppose we are asked to retrieve just the movie title.  How would we write Ruby code to do that?

```ruby
movie[:title]
```

This expression will hand back the text value `"Apollo 13"`.

We use the square brackets to retrieve an element, just like we did with an array.  However, instead of providing a zero-based position index, we can simply provide the key that we know has been associated with the value.

### Adding More Elements

Hashes can grow and shrink at your command.  Let's add another attribute to keep track of the length of the movie, in minutes:

```ruby
movie[:duration] = 140
```

Here we begin as if we are accessing the new `:duration` key, but we use the assignment expression `= 140` to indicate that we want to associate `140` with the key `:duration`.

If we now ask the console to tell us the full value of the `movie` variable, we can see that the `:duration` has been added:

```ruby
movie
=> { title: 'Apollo 13', year: 1995, rating: 7.6, duration: 140 }
```

### Hash Playground

[There are lots of things you can with hashes.](http://www.ruby-doc.org/core-2.1.1/Hash.html).  Here are some methods you can try to help motivate you to learn more about how to manipulate Ruby hashes.

```ruby
movie.keys
movie.delete(:title)
```


