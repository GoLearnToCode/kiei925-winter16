# Cheat Sheet: RESTful Routing

**REST** stands for *Representational State Transfer*, first proposed (or identified) by [Roy Fielding](http://www.ics.uci.edu/~fielding/pubs/dissertation/fielding_dissertation.pdf).  There's a lot of technical jargon behind it, but it boils down to something really simple.  But before we get to that, let's first talk about how the web works.

### The HTTP Request-Response Cycle

When we use browser software, we are able to visit websites produced by millions of different organizations.  Most of those websites were created after the browser software was created.  How does our browser "know" how to display a website that wasn't in existence when its software developers put it together?

Here's another way of asking the same question: When we type a URL into our browser's address bar, how does the browser know what to show on our screen?

Browsers appear to "know" about every website on the planet because they simply follow the rules of the internet.  Here's how it works:

1. You enter a URL in the address bar.  (Or you click a link, which amounts to the same thing).
2. The browser sends a *request* to that URL, asking for it's home page.
3. The server sends back a *response*, which is the HTML that the browser should display.
4. The HTML can contain links embedded within it, which provide the user with more URLs to discover.

Now that we know that *browsers send requests* and *servers send responses*, we can unpack the request and response a little more.

### REST

Until now we've considered the entire "request" to be the URL in the address bar (or the `href` attribute of an `<a>` element).

That's not the whole story.  Web requests actually consist of *two* parts:

1. a resource locator (the URL)
2. an HTTP Method

URLs do one thing: *locate*, or *identify*, a resource.  And *resources* are nouns.  Books. Users. Messages. Friends.  Tweets. Photos. HTTP Methods, on the other hand, indicate the action we want to take against that resource.  Many developers refer to them as *verbs*.

HTTP allows us to define new nouns anytime we want.  There are an infinite number of possible resources.  New resources spring up every day as new websites appear and expose new URLs.  The wonderful thing about the internet is that anyone on the planet can invent new resources and make the available to everyone else on the web.

But now here comes the genius of HTTP.  Are you ready?  Sitting down?

HTTP defines a **finite set of verbs**.  Four, to be exact:

1. GET
2. POST
3. PATCH
4. DELETE

Each request is the combination of exactly one verb + one noun.

Everything we do on the internet is accomplished with HTTP requests, and each request uses one verb with one noun.  When we do this properly - each URL is a noun-like resource, and the appropriate verb is sent along with it - we are conforming to "RESTful" practices.

What did you do today on the web?  Checked your email? Bought an airline ticket? Posted a message on Facebook?  View your checking account balance?  They're all possible because the browser combines an HTTP verb (method) with an HTTP noun (resource).

### HTTP Methods

Each of the four HTTP methods (or verbs) have a twin in a parallel universe.  Remember CRUD? Here's how the HTTP Methods correspond to those:

|HTTP Method/Verb|Database Action|
|----|-----|
|GET|Read|
|POST|Create|
|PATCH|Update|
|DELETE|Delete|


