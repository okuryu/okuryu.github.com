---
layout: post
title: PhantomJS 1.6 Changes
description: Pick up some points of PhantomJS 1.6
---

Recently, PhantomJS 1.6 has released. PhantomJS has a flower name for each releases,
this version has "Lavender". This version is minor update, but it's has some new
features in view of the release note, I tried a few points.

## Support for passing arguments to WebPage's evaluate

You can now pass the variable to the callback function of page.evaluate.

	var prefix = 'Title:',
	  result;
	
	result = page.evaluate(function (p) {
	  return p + document.title;
	}, prefix);
	
	console.log(result);

## Callbacks for JavaScript onConfirm and onPrompt

onConfirm, onPrompt of JavaScript callbacks has been added.

	var result;
	
	page.onConfirm = function(msg) {
	  console.log(msg);
	};
	
	result = page.evaluate(function() {
	  return window.confirm('Hello Confirm!');
	});

## Support for Cookies handling

Cookie data has been supported. Until now was not only pass in the options of
the command of PhantomJS, but you can now be specified in the page object.

	page.cookies = [{
	  'name': 'Cookie-Name',
	  'value': 'Cookie-Value',
	  'domain': 'localhost'
	}];

## 'os' object to the system module

The 'os' object has been added into system module.

	var os = require('system').os;
	
	for (var p in os) {
	  console.log(p + ': ' + os[p]);
	}

The result is like this:

	architecture: 32bit
	name: mac
	version: 10.7 (Lion)

## Support for asynchronous evaluation

You can now asynchronously evaluation of the page. This is useful if you don't
need the results of evaluation.

	page.evaluateAsync(function () {
	  // do something
	});

Complete changes to [release note][releasenote] since it is written, please check it out.

[releasenote]: http://code.google.com/p/phantomjs/wiki/ReleaseNotes
