--- 
layout: post
title: "Introduction to Google Guava's Splitter class"
categories: posts
tags: []
---
The <code>Splitter</code> class takes a common, and what should not have to be verbose, exercise and makes it easy and readable. Let us start with a scenario, you have a list of key value pairs that you need to parse into a map. We are also going to assume the input could be malformed with empty entries and extra spaces. For the sake of this example, let us use names and user ids.

<div class="CodeRay">
  <div class="code"><pre>&quot;dave:123, john:314,, matt:989&quot;</pre></div>
</div>


Now, how this is typically handled:

<script src="https://gist.github.com/1271799.js"></script>

This ends up being rather verbose and also error prone. We will see how the <code>Splitter</code> class makes this much easier and readable.

## Starting with the basics

The simplest example of the <code>Splitter</code> is parsing a standard comma separated list.

<script src="https://gist.github.com/1271773.js"></script>

Pretty straightforward. In addition to a string separator, the <code>Splitter.on</code> function can also use a <code>char</code>, <code>CharSequence</code>, or a <code>Pattern</code>. The API provides a convenience method <code>Splitter.onPattern</code> that will turn a <code>String</code> into a java <code>Pattern</code>.

## Utilities to sanitize the input

We saw in the initial scenario a poorly formatted string that required us to check for <code>null</code> and trim at various points to clean up the input. The <code>Splitter</code> class comes with the utility functions <code>omitEmptyStrings</code> and <code>trimResults</code> to take away some of that boilerplate code.

<script src="https://gist.github.com/1271776.js"></script>

Another benefit of using the utility functions to clean up the split string is readability. When someone is reading your code, it is much easier to understand what is happening when seeing <code>omitEmptyStrings</code> and <code>trimResults</code> versus checks for <code>null</code>, checks for empty string, and various trim calls.

## Using the MapSplitter (new in Guava 10.0)

The MapSplitter allows you to take a list of key value pairs and easily turn it into a Java Map. Well, that sounds great for solving our initial scenario, let us see it in action.

<script src="https://gist.github.com/1271761.js"></script>

That looks much better. We removed the loop, the input was sanitized, we threw out any empty strings, and we broke up the separated values into key/value pairs. It also reads a lot better:

<em>Split a string on comma, omit empty strings, trim those results, then use colon as a key value separator. With these rules, split <code>stringToSplit</code></em>

This is much easier to read than our initial version. You can read the full documentation on the <code>Splitter</code> class <a href="http://docs.guava-libraries.googlecode.com/git-history/v10.0/javadoc/index.html">here</a>.
