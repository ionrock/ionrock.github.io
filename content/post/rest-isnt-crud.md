---
title: "Rest Isn't Crud"
date: 2024-06-12
draft: true
---

I'm sure you've heard of REST. One thing that always bothers me is when I hear people describe REST in terms of CRUD. REST isn't CRUD!

My guess is that the examples have spoken louder than the principles. When REST came about as an development pattern, [Rails](https://rubyonrails.com) was really popular. Rails promoted a Model View Controller (MVC) paradigm for organizing code. MVC wasn't new, but for a lot of people, the constraints of MVC was a breath of fresh air. It got people thinking in terms of models being created, updated, and deleted. URLs became structured instead of being an endpoint with tons of query string parameters. When REST became popular, people associated with MVC patterns and naturally made the connection with CRUD. But, REST didn't come from the world of Rails.

REST became really popular soon after the blogging world took off. RSS helped to create a personally curated content stream you could consume and enjoy. Web Standards were another theme during this time with the goal of making the HTML programmatically reliable via XHTML. These were all representative (pun intended) of the true power of REST. In addition to RSS, there was Atom, an arguably better designed feed format, that ended up with an API specification (AtomPub) that provided a programmatic, RESTful, interface.

AtomPub was pretty simple. For example, to create a new blog post (AtomPub wasn't just for blogs, but that was the initial use case), you'd `POST` to a collection at that collection's URL.

```
POST /edit/ HTTP/1.1
Host: example.org
User-Agent: Thingio/1.0
Authorization: Basic ZGFmZnk6c2VjZXJldA==
Content-Type: application/atom+xml;type=entry
Content-Length: nnn
Slug: First Post

<?xml version="1.0"?>
<entry xmlns="http://www.w3.org/2005/Atom">
  <title>Atom-Powered Robots Run Amok</title>
  <id>urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a</id>
  <updated>2003-12-13T18:30:02Z</updated>
  <author><name>John Doe</name></author>
  <content>Some text.</content>
</entry>
```

The response would return a success code and the location of the new entry.

```
HTTP/1.1 201 Created
Date: Fri, 7 Oct 2005 17:17:11 GMT
Content-Length: nnn
Content-Type: application/atom+xml;type=entry;charset="utf-8"
Location: http://example.org/edit/first-post.atom
ETag: "c180de84f991g8"
```

Now, what I want to bring your attention to is the `Location: http://example.org/edit/first-post.atom` in the response. Back in the day, we typically had a URL pattern for blogs like `YYYY/MM/DD/slug`. When you `POST` to an AtomPub server, your leaving it up to the server to decide where that Entry should land. More generally though, the **`POST` means you're giving information to the server to do what it wants**. The server doesn't have to create anything. The server can use what it wants from the request body and, you as the client, are not in control. Looking at the example above, the `Location` could have been anything and didn't have to use the `Slug` header to create the `first-post.atom` that resulted.

Where things get more "RESTful" is in the `PUT` semantics. This was heavily inspired by an earlier server spec, [WebDAV](https://en.wikipedia.org/wiki/WebDAV). Generally, WebDAV allowed you to take documents and put them on the web. I say "put" because this was WebDAV's primary interface, `PUT`. If I had a web server that supported WebDAV, I could `PUT` some HTML file to a URL and that would then be served by the web server. In practice, this became a really helpful file storage protocol for internal networks and file shares.

To recap, `POST` sends data to a server and gives the server control over what happens to it. `PUT` takes a document and intends that document to replace or create the current representation at the specified URL.

The last element of REST that gets lost in the association with CRUD is the idea of a document. REST came about when XML was widely used. I'd say XML was popular, but the reality is most people weren't fans of XML. People made a similar mistake with XML in associating it with configuration and serializing code, instead of using it as a document format. XML has a very powerful capability to represent different media types within the same document. For something like a blog post, this meant you could use XML to maintain metadata, content, and even binary data, all in the same document. There were also interesting technologies surrounding XML that made this multi-medium facility really powerful. XPath let you find specific elements, and when coupled with XSLT, you could create new documents with different formats, that didn't need to be XML at all.

Much of the XML capabilities were similar in HTML and HTML was originally a primary target of REST. Prior to REST, Web Services had gained some popularity. Web Services were basically like gRPC with the difference being instead of protobufs, it used a really complicated suite of XML formats that didn't interoperate very well across platforms. Architecturally, the idea was you could call functions remotely. Most sites didn't offer a Web Service interface, so people wrote programs to grab HTML and made requests as though they were in a web browser. That method effectively became REST to folks.

When things became formalized, people seemed to miss out on the value a document provides in the whole system. Returning to AtomPub, your server could use content negotiation to return a PDF of blog post by adding an accept header. Query params could be used to filter a collection list or grab specific information from a specific document. HTTP caching made all these document manipulations reasonably performant at scale. It wasn't always convenient because you would almost always needed take the document and convert it to something your program could use. This often meant dealing with bad HTML and XML technologies that weren't always easy to use. The desire to easily take a response and turn it into a data structure ended up trumping the benefits of utilizing the representation of the data as a document and we ended up with REST meaning CRUD.

Thankfully, there are those that have started to [challenge the status quo](https://hypermedia.systems/) and recognize the benefit of leveraging the representation of the data.

So, why does it event matter?

When you start associating REST with the representations of data it can open your mind to simpler solutions. Instead of constantly transforming data, you can just return a representation that makes sense in your limited use case and feel good about it. You don't have to use XML/HTML either. You can use JSON. The semantics of `PUT` and `POST` also start to become more applicable. When you need to control things as a client, `PUT` is a potentially better way to create something, especially if you need to control the location. When you need flexibility in how you create things, `POST` gives you the freedom to let your server act robustly.

GraphQL is an interesting side note because in some ways, it was a natural progression for REST. GraphQL works well when the query string parameters become too much and you need to specify precisely what the output looks like. The problem, from my perspective, is that it [disconnected URL from the representation](https://graphql.org/learn/serving-over-http/#api-endpoint). This feels like a missed opportunity where GraphQL could have been the standard means of normalizing content negotiation and smoothing over the challenges that can arise from updates. PATCH was always a struggle and [QUERY](https://httpwg.org/http-extensions/draft-ietf-httpbis-safe-method-w-body.html) is a natural fit. 

At the end of the day I hope the message sent by the Hypermedia folks helps expand how people build APIs. They will always get messy over time, but thinking outside the bounds of CRUD may help find a work around. 

Beyond opening your mind to new concepts though, I secretly hope that I stop hearing people saying `POST == create`.
