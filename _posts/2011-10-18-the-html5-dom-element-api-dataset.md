--- 
layout: post
title: "The HTML5 DOM Element API: Dataset"
categories: posts
tags: []
---
Datasets are one of the new Element features added with the HTML5 spec. They allow you to add arbitrary attributes to DOM Elements that can be easily accessed and modified via JavaScript. These attributes are great for adding additional information for projects such as photo galleries that can use the attributes to enhance the display.

## Using data attributes on elements

Datasets are added to an element via element attributes. A dataset attribute is prefixed by <code>data-</code> and followed by the name. For example, <code>data-author</code>.

For this post, we are going to use a photo gallery as an example of when you might want to use datasets to add additional markup to your HTML. To start, let us create the first <code>div</code> with attributes that define the author, location, and date of the photo. Here is the markup:

<script src="https://gist.github.com/1294430.js"></script>

As you can see, the three items we want in the dataset are prefixed by <code>data-</code> and are assigned a value the same way as any other HTML attribute.

## Accessing an element&rsquo;s dataset

To access the dataset of an element, simply use the attribute <code>dataset</code>. Here is a quick example.

<script src="https://gist.github.com/1294438.js"></script>

The <code>dataset</code> attribute returns a <a href="https://developer.mozilla.org/en/DOM/DOMStringMap">DOMStringMap</a>, a new datatype added for datasets. Note: hyphenated attribute names are turned into camel case for JavaScript access.

## Modifying and removing an element&rsquo;s dataset

Modifying an item in the dataset is very easy, just assign the property in the dataset a new value.

<script src="https://gist.github.com/1294440.js"></script>

Deleting is equally easy, just use the keyword <code>delete</code> and specify the property of the dataset to delete.

<script src="https://gist.github.com/1294441.js"></script>

## Using data attributes with CSS

Like other HTML Element attributes, dataset attributes can be used as part of CSS selectors. Adding a blue background to all divs with Dave as the author looks like the following:

<script src="https://gist.github.com/1294516.js"></script>

Datasets provide an easy way to associate little bits of meta data with your HTML tags and allows easy access from your JavaScript. For more intensive JavaScript applications you will still be better off using JavaScript objects to hold your state. However, for quick projects like a photo gallery, dataset attributes provide easy access to additional data for each element. As far as browser support, here is the <a href="http://caniuse.com/#search=dataset">caniuse</a> page.
