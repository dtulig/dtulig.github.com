--- 
layout: post
title: "Introduction to Google Guava's Joiner class"
categories: posts
tags: []
---
The <code>Joiner</code> class performs the complementary function of the <code>Splitter</code> class. The <code>Joiner</code> class will join an <code>Iterable</code>, an array, or a variable argument list using a given separator in between them.

## Starting with the basics

The basic usage of the <code>Joiner</code> uses the <code>on</code> function and then by calling <code>join</code> with an array or <code>Iterator</code> object. To demonstrate this, let us use a <code>Set</code> of names to create a comma separated list.

<script src="https://gist.github.com/1277164.js"></script>

## Dealing with nulls

Like the <code>Splitter</code>, the <code>Joiner</code> comes with a couple of utilities for dealing with <code>null</code> in the input. The first is the <code>skipNulls</code> function that will return a <code>Joiner</code> which will automatically skip over any nulls it encounters when iterating over the elements. The second is the <code>useForNull</code> function which will use the parameter it was given in place of nulls. Here are examples of using each one:

<script src="https://gist.github.com/1277178.js"></script>

If you use both the <code>skipNulls</code> and <code>useForNull</code> on the same joiner, it will throw an <code>UnsupportedOperationException</code>.

## Using the <code>Joiner</code> class to build up a <code>StringBuilder</code>

In addition to joining a <code>String</code> all at the same time, you can build it up instead using a <code>StringBuilder</code>. The <code>appendTo</code> function of the <code>Joiner</code> takes the same arguments as the <code>join</code> function: an Iterable, array, or argument list an will work for both <code>StringBuilders</code> and any <code>Appendable</code> object. One caveat of this function is that it will only add the separator between elements within each function call. Below is an example of using it with a <code>StringBuilder</code>.

<script src="https://gist.github.com/1277255.js"></script>

As you can see, the commas were only added in between elements in the same <code>appendTo</code> call which is why <code>johndanmatt</code> was not separated.

## Using the MapJoiner (new in Guava 10.0)

A good example of using a <code>MapJoiner</code> is to create a query string out of a <code>Map</code> of query parameters. Let us use the following map:

<div class="CodeRay">
  <div class="code"><pre>{&quot;param&quot;: &quot;v&quot;, &quot;p2&quot;: &quot;v2&quot;, &quot;q&quot;: &quot;java&quot;}</pre></div>
</div>


And the code:

<script src="https://gist.github.com/1277093.js"></script>

The <code>MapJoiner</code> does not have utilities for trimming and cleaning up the strings, so that will have to be done while building the <code>Map</code>. You can read the full documentation on the <code>Joiner</code> class <a href="http://docs.guava-libraries.googlecode.com/git-history/v10.0.1/javadoc/index.html">here</a>.

<em><a href="/blog/introduction-to-google-guavas-splitter-class">View the previous post on Google Guava&rsquo;s Splitter class</a></em>
