# Cheat Sheet: Model Associations

There are two kinds of associations:

1. **One-to-Many**.  An album has many songs.  A blog post has many comments.  A user posts many tweets.
1. **Many-to-Many**.  A movie has many actors, and an actor can perform in many movies.  An author can write many books, and a book can be co-written by many authors.  An article can have many tags, and a tag can be put on many articles.

Implementing a one-to-many association is easy.  Implementing a many-to-many association is achieved by breaking it down into two one-to-many associations.

### The One-to-Many Recipe

To implement a one-to-many association:

1. Identify which model is the "one" and which model is the "many".
1. The model at the "many" end needs a **foreign key column** to associate it to the "one" owner.

**Be sure to stick to Rails naming conventions.** Refer to [How To: Start Domain Modeling](domain_modeling) for details.

```
Album:
  title: string
  artist: string
  year: integer

Song:
  title: string
  album_id: integer
```

Example data tables:

<table class="table table-bordered">
  <thead>
    <tr>
      <td colspan="5" style="background: #fffbce">albums</td>
    </tr>
    <tr>
      <th>id<br>(integer)</th>
      <th>title<br>(string)</th>
      <th>artist<br>(string)</th>
      <th>year<br>(integer)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>Abbey Road</td>
      <td>The Beatles</td>
      <td>1969</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Thriller</td>
      <td>Michael Jackson</td>
      <td>1982</td>
    </tr>
  </tbody>
</table>

<table class="table table-bordered">
  <thead>
    <tr>
      <td colspan="5" style="background: #fffbce">songs</td>
    </tr>
    <tr>
      <th>id<br>(integer)</th>
      <th>title<br>(string)</th>
      <th>album_id<br>(integer)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>Come Together</td>
      <td>1</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Something</td>
      <td>1</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Something</td>
      <td>1</td>
    </tr>
  </tbody>
</table>

### The Many-to-Many Recipe

To implement a many-to-many association:

1. Identify the "missing model" that represents the real-world connection between the models.  This is your new "join" model.  You now have three models that need to be connected together.
1. Now, reduce the problem to two one-two-many associations:
  1. The join model gets **two foreign keys**.
  1. The other models need **no foreign keys**.

**Be sure to stick to Rails naming conventions.** Refer to [How To: Start Domain Modeling](domain_modeling) for details.

```
Book:
  title: string
  isbn: string
  cover_photo_url: string

Work:
  book_id: integer
  author_id: integer

Author:
  name: string
  bio: text
  photo_url: string
```
