--- 
layout: post
title: "The HTML5 DOM Element API: classList"
categories: posts
tags: []
---
The <code>classList</code> object is a set of functions that helps you manipulate the <code>class</code> attribute on a node. It provides functionality that allows you to add a class to the node, remove a class, find out if a node contains a class, and lets you toggle a class. It is a pretty simple API to interact with so let us run through an example that uses the available functions.

Starting HTML:

<script src="https://gist.github.com/1347084.js"></script>

And now for the JavaScript:

<script src="https://gist.github.com/1347059.js"></script>

This is something that JavaScript libraries have been helping us with for awhile and it is great to see it make its entrance as a native API. Unfortunately, support is still lagging a bit. You will find it available in Firefox and Chrome; the rest of the browsers only have it in more recent versions and IE does not have support for it at all, at the time of this post. Here is the full <a href="http://caniuse.com/#search=classList">caniuse</a> page.
