# Cheat Sheet: Ruby Data Containers, Part 3: Loops

When we have a collection of data contained in an array, we often want to take a particular action with each and every element inside the array.

Consider this Ruby array that's embedded inside an HTML view template:

```erb
<%% teams = ["Chicago", "Boston", "Los Angeles"] %>
```

Suppose we'd like to transform this data into an HTML bullet list like this:

<div class="well">
<ul>
  <li>Chicago</li>
  <li>Boston</li>
  <li>Los Angeles</li>
</ul>
</div>

What Ruby code could we write to do that?

Think about it for a minute.  Can you figure it out?

### Loops

A _loop_ is said to occur when we ask the computer do perform the same action many times in a row.

Here is some HTML with embedded Ruby that will create six bullet items with the word "Hello":

```erb
<ul>
  <%% 6.times do %>
    <li>Hello</li>
  <%% end %>
</ul>
```
When this view is rendered, the HTML output will look like this:

<div class="well">
<ul>
  <li>Hello</li>
  <li>Hello</li>
  <li>Hello</li>
  <li>Hello</li>
  <li>Hello</li>
  <li>Hello</li>
</ul>
</div>

We say that the computer _looped_ over the `<li>Hello</li>` instruction 6 times.

Normally we don't want to repeat the exact same text each time.  When the text we want is stored in an array, we can have the computer pull text from the array:

```erb
<%% teams = ["Chicago", "Boston", "Los Angeles"] %>
<ul>
  <%% teams.each do |city| %>
    <li><%%= city %></li>
  <%% end %>
</ul>
```
Notice how we use the `.each` method to indicate that we want to loop over each element in the `teams` array.  We use the double-bar syntax `|city|` to tell the computer to store each element's value in a variable named `city` for each turn through the loop.

Now we will get HTML that looks like this:

<div class="well">
<ul>
  <li>Chicago</li>
  <li>Boston</li>
  <li>Los Angeles</li>
</ul>
</div>

