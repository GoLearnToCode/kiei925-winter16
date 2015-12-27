# How To: Start Domain Modeling

When we build an app, we represent real-world entities inside the virtualized world of our software.  Our job as software developers is to represent those real-world things as best we can.  How do we begin?  We first identify all of those entities which comprise our particular domain of concern, as well as the interconnections that exist between them.

Identifying all of the real-world things that our software must contain is harder than it sounds.  But here's the good news.  We do not have to figure out our entire domain model up front.  Instead, we start by identifying only those entities that are most central and most obvious to our application.  Identifying the first few models is more than enough to begin the initial version of our app.

From now on, we will call each real-world entity a _model_.

And all of our models, together with all of their relationships, is called our _domain model_.

### Models and Their Attributes

Most models have data associated with them.

For example, suppose we identify a _User_ as one of our models.  Users do not exist in theory.  Users exist in our real world. They are the actual people that use our software.

So our next step is to figure out what data we need to keep track of when we think of our users.  We will probably need to track:

* their name
* email address
* password
* anything else that belongs in a typical user profile.

The data set pertaining to a given model is called the model's _attributes_.

Here's another example.  Suppose we're building an online newspaper.  Can you name at least one model that we will need?

How about articles?  Ok, what data would we need to keep track of an article?

* headline
* body text of the article
* author's name
* date

Hopefully you're getting the idea that to start building our domain model, we identify _models_ - real-world things that our software must emulate - and then identify the model's primary _attributes_.

### Database-Backed Models

A model and its attributes can be neatly represented in a _database table_.  If you're familiar with an Excel spreadsheet, then you already know what a database table is: a set of rows and columns.

* Each column represents a particular model _attribute_
* Each row represents a unique model _instance_
* All rows share exactly the same set of columns

Each model will need a different table, because the column definitions will be different for every model.

### Naming Conventions

While there exist several plausible approaches to model and attribute representation, we will adopt conventions set forth by the Rails framework.

  1. Model names will be capitalized and preferably one word, i.e. `Product`, `Book`, `Movie`.  Multi-word names are joined together with capital letters into a single word identifier: `ProductCategory`, `BuildingMaterial`.
  1. Model names must be **singular nouns**: Book, Song, Movie, Person.
  1. Table names must be **pluralized model names** and **lowercase** only: `books`, `songs`, `movies`, `people`.  If the model used multiple words, underscores are used: `product_categories`, `building_materials`.
  1. Attribute names are **lowercase only**: `title`, `first_name`, `city`.
  1. Every table must have an attribute named `id`.
  1. Every attribute must have a specified data type: numeric (integer or float), textual (string or text), date, time, or boolean.
  1. Attributes can hold a single atomic value only, not a list of values.
  1. Attributes which are intended to store the identifier of a row from a different table are called _foreign keys_ and use the `_id` suffix: `director_id`, `product_id`, `movie_id`.

Model attributes are implemented as table columns.  So from now on, we will use the words _column_ and _attribute_ interchangably.

### Column Types You Can Use

<table class="table table-bordered">
  <thead>
    <tr>
      <td colspan="3" style="background: #c5ffe0">Column Data Types</td>
    </tr>
    <tr>
      <th>Type</th>
      <th>Description</th>
      <th>Notes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>integer</td>
      <td>An integer</td>
      <td>Good for row identifiers, prices, and simple numbers</td>
    </tr>
    <tr>
      <td>string</td>
      <td>Short text up to 250 characters</td>
      <td>Good for a headline, title, or tweet</td>
    </tr>
    <tr>
      <td>text</td>
      <td>Long text, up to 2Gb</td>
      <td>An entire article or book</td>
    </tr>
    <tr>
      <td>boolean</td>
      <td><b>true</b> or <b>false</b></td>
      <td>Good for checkboxes, on/off states, yes/no answers, etc.</td>
    </tr>
    <tr>
      <td>datetime</td>
      <td>A date with a timestamp</td>
      <td></td>
    </tr>
    <tr>
      <td>date</td>
      <td>Just the date</td>
      <td></td>
    </tr>
    <tr>
      <td>float</td>
      <td>A number with decimal point</td>
      <td>If you need non-integer numerical values</td>
    </tr>
  </tbody>
</table>

### Example: Data Tables for imdb.com (initial version)

<table class="table table-bordered">
  <thead>
    <tr>
      <td colspan="5" style="background: #fffbce">movies</td>
    </tr>
    <tr>
      <th>id<br>(integer)</th>
      <th>title<br>(string)</th>
      <th>director_id<br>(integer)</th>
      <th>year<br>(integer)</th>
      <th>synopsis<br>(text)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>Raiders of the Lost Ark</td>
      <td>2</td>
      <td>1983</td>
      <td>I hate rats.</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Apollo 13</td>
      <td>1</td>
      <td>1995</td>
      <td>Wonderful documentary about computers, people, and error messages.</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Lincoln</td>
      <td>2</td>
      <td>2012</td>
      <td>He dies at the end.  (Oops, should have said "spoiler alert")</td>
    </tr>
  </tbody>
</table>

<table class="table table-bordered">
  <thead>
    <tr>
      <td colspan="5" style="background: #fffbce">directors</td>
    </tr>
    <tr>
      <th>id<br>(integer)</th>
      <th>name<br>(string)</th>
      <th>photo_url<br>(string)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>Ron Howard</td>
      <td>http://ia.media-imdb.com/images/M/MV5BMTkzMDczMjUxNF5BMl5BanBnXkFtZTcwODY1Njk5Mg@@._V1_SX214_CR0,0,214,317_.jpg</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Steven Spielberg</td>
      <td>http://ia.media-imdb.com/images/M/MV5BMTY1NjAzNzE1MV5BMl5BanBnXkFtZTYwNTk0ODc0._V1_SX214_CR0,0,214,317_.jpg</td>
    </tr>
  </tbody>
</table>

