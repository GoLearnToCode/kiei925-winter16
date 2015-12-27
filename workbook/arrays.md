# Cheat Sheet: Ruby Data Containers, Part 1: Arrays

Every computer program manages data of one kind of another.  Every kind of software model -- users, movies, shopping carts, bank accounts, credit cards, search results, etc. -- consists of atomic data elements.  The atomic data elements are numbers, text, dates, and boolean (true/false) values.  We then compose higher-order data models, like a movie model, from these atomic elements.

Orthogonal to the concept of model making is the notion of data _collections_, or simple lists.  In fact, most web pages can be boiled down to managing a list of things (or, for more complex pages, lists of lists of things).

There are two primary _data containers_ that Ruby provides out-of-the-box for us when we need to manage a list of things:

1. Arrays
2. Hashes

This cheat sheet will focus on how to manage a simple list using an array.

Find a Rails application that you've created, start the `rails console` and follow along.

### Creating a List using an Array

Whenever we have a list of things where **order matters**, we use a Ruby Array.

Say we need to manage a list of numbers representing last night's winning Pick 3 lottery numbers.  The winning numbers were `6`, `8`, and `1`, in that order.  How can we have the computer represent this sequence of numbers?

```ruby
lottery = [6, 8, 1]
```

Here we create a variable named `lottery` that will hold our set of numbers.  We use the square brackets `[ ]` to tell Ruby that we want to use an `Array` to hold our list of numbers.  An array will preserve the order and allow us to access individual elements of the array whenever we need them.

### How Many Elements?

We can determine the number of elements inside an array by using any of the following methods:

```ruby
lottery.count
lottery.size
lottery.length
```

These are all synonyms for each other.  Use whichever one feels most natural.

### Accessing Individual Elements

Suppose we are asked to retrieve the first winning digit from the `lottery` variable.  How would we write Ruby code to do that?  Here is one way:

```ruby
lottery.first
```

The `.first` method of an array object will always hand back the first element inside the array.  What if we are asked for the final winning number?

```ruby
lottery.last
```
That should return the value `1` and display it in your console.

What about the middle number?  Unfortunately, there is no `.middle` method.  Instead, we can use the general form of array element access, which is to use a zero-based position index:

```ruby
lottery[1]
```
That should return the value `8`.

### Adding More Elements

Arrays can grow and shrink at your command.  We can turn the Pick-3 number into a pick 4 by appending another element with the `.push` method:

```ruby
lottery.push(5)
```

We can ask the console to report the full contents of the `lottery` variable:

```ruby
lottery
=> [6, 8, 1, 5]

lottery.count
=> 4
```

### Array Playground

[There are lots of things you can with arrays.](http://www.ruby-doc.org/core-2.1.1/Array.html).  Here are some methods you can try to help motivate you to learn more about how to manipulate Ruby arrays.

```ruby
sports = ["Hockey", "Baseball", "Soccer"]

sports.sample
sports.sample(2)
sports.reverse
sports.sort
```


