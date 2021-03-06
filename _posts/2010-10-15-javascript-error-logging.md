--- 
layout: post
title: "JavaScript Error Logging"
meta: JavaScript Error Logging
categories: posts
tags: []
---

A useful technique that I have been using to help keep track of JavaScript errors has been to use the <code>OnError</code> event to help log client side errors that slip through the testing process. In addition to the properties that come with the JavaScript exception (the error message, the url of the script, and the line number) I log the url of the page that they were on when the problem occurred which makes reproducing the situation much easier. Another nice little benefit of catching errors through my own callback is being able to suppress the error message from the user, in some browsers this can be as invasive as a popup (IE). On to some code.

<script src="https://gist.github.com/621590.js"></script>

The code should be fairly straightforward. The <code>OnError</code> event is assigned my own error handler. Whenever a JavaScript error occurs a request is sent to <code>/rpc/client-error-log</code> with the details of the problem. The <code>return true</code> at the end of <code>errorHandler</code> suppresses the error message from the user. On the server side, I log the error that occurred. Every morning I send myself an email with all the error messages for the past 24 hours. A fair number of them are problems that I cannot, or have not, figured out how to fix such as &ldquo;Error loading script&rdquo;. Although when I occasionally introduce a bug into the wild, this gives me all the information I need to reproduce and fix it (usually).
