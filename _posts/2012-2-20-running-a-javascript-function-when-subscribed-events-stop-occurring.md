---
title: "Running a JavaScript function when subscribed events stop occurring"
tags:
  - JavaScript
---


Maybe this is [well-known](http://stackoverflow.com/questions/3015319/jquery-javascript-settimeout-cleartimeout) to the JavaScript coding community — below is a simple technique I've found that runs a block of JavaScript when subscribed events stop firing. Full disclosure, I stole this from [Hugoware](http://hugoware.net/). If he stole it from someone else… ;)

## Use Case

A user is entering text into a text box. The user stops typing for a period of time, tabs or clicks out of the text box, or is otherwise done using the text box. When the user is done, server side validation is done (such as checking for uniqueness of a username on a sign-up form).

## Solution

Attach a set of events to the text box that capture when the user is making a change, or leaving the text box. Every time the event fires, create a function that contains the functionality you want, to be fired on a timeout. If the event is fired again, cancel the existing function.

In code (using jQuery 1.7 syntax):

	var timeout;
	('#mytextbox').on('focusout blur keyup change', function () {
	    if (timeout) {
	        window.clearTimeout(timeout);
	    }
	    timeout = window.setTimeout(function () {
	        // Perform server-side validation here
	    }, 1000);
	);

## Bonus: jQuery plugin

While the above code is pretty simple, if you want to use this pattern a few times on the same page, it can lead to some duplicated code and multiple variables to hold the timeout. So I'm solving that with a jQuery plugin. Behold, jquery.onidle.js:

	$('#mytextbox').onidle('focusout blur keyup change', 1000, function () {
	    // Your idle functionality here
	});

For more details on the plugin, visit its [GitHub page](https://github.com/Fammy/jquery.onidle).