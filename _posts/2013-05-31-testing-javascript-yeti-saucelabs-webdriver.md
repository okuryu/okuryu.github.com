---
layout: post
title: Testing JavaScript with Yeti and Sauce Labs WebDriver
description: How to test your JavaScript with Yeti and Sauce Labs.
---

We've recently been quite busy developing a number of JavaScript testing
environments, such as test frameworks and test runners. [Yeti][yeticx],
developed by the YUI team, is one of the test runners. As for the available
test frameworks, Yeti supports the major libraries—not only YUI Test, but
QUnit, Jasmine, and Mocha. I've shown examples previously where Yeti and
QUnit were used together.

<img src="/img/saucelabs-yui.png" alt="">

On top of JavaScript testing, we can't forget the devices and browsers on
which the testing is being done in the first place. With the spread of so
many different types of mobile devices and so many OSes and browsers in
development, it's become important to carry out tests on the actual browsers.
In these conditions, services have appeared that allow you to open and operate
the actual browsers online. Today, I'd like to show you a test using one of
those services, [Sauce Labs][saucelabs]. Sauce Labs is a cloud service that
offers many different mobile and desktop browser environments. Also, one of
Sauce Labs' major features is that it supports Selenium WebDriver protocol.
Just like Yeti, since WebDriver protocol is supported, you can boot the
browser on the cloud through the command line and run a JavaScript test.

First, You can sign up easy Sauce Labs account if you doesn't have a Sauce Labs
account. Sauce Labs provides some free and paid plans. Also there is
"Open Sauce" plan, this is very kind and helping plan for OSS developers like
you.

Sign up when you're done, let's prepare for the testing environment.
Check your access key and download `Sauce-Connect.jar` file from
[Sauce Connect guide][sauce-connect].

Start Sauce Connect:

	java -jar Sauce-Connect.jar <username> <access key>

Install Yeti via npm command if you haven't install yet.

	npm install -g yeti

Start Yeti hub server while specify Sauce Labs WebDriver endpoint:

	yeti --server --wd-url http://<username>:<access key>@ondemand.saucelabs.com:80
	Yeti Hub started. LAN: http://10.0.1.13:9000
	                  Local: http://localhost:9000

And, Launch browser you like while specify a test file:

	yeti --browser chrome src/date/tests/unit/*.html
	Waiting for Hub to launch browsers...
	  Agent connected: Chrome (26.0.1410.64) / Windows 7 from 10.0.1.13
	✓ Testing started on Chrome (26.0.1410.64) / Windows 7
	✓ Agent completed: Chrome (26.0.1410.64) / Windows 7
	✓ 22 tests passed! (35 seconds)
	  Agent disconnected: Chrome (26.0.1410.64) / Windows 7 from 10.0.1.13

That's all. It's able to test on the browser in the cloud even if you don't
have it!

[saucelabs]: https://saucelabs.com/
[sauce-connect]: https://saucelabs.com/docs/connect
[yeticx]: http://yeti.cx/
