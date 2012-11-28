---
layout: post
title: How to run Yeti with QUnit testing
description: Introduce to the way to run Yeti with QUnit testing.
---

[QUnit][qunit] is a JavaScript Unit Testing framework by jQuery project. I
would like to introduce to the way to run [Yeti][yeti] with QUnit testing
since latest Yeti Supporting QUnit test cases.

At first, setup minimum QUnit test case.

	<!DOCTYPE html>
	<html>
	<head>
	  <meta charset="utf-8">
	  <title>QUnit Example</title>
	  <link rel="stylesheet" href="/resources/qunit.css">
	</head>
	<body>
	  <div id="qunit"></div>
	  <script src="/resources/qunit.js"></script>
	  <script src="/resources/tests.js"></script>
	</body>
	</html>

And, create test.js just like this.

	test( "hello test", function() {
	  ok( 1 == "1", "Passed!" );
	});

Install Yeti via npm command.

	$ npm install -g yeti

Start Yeti as server mode. Yeti Hub waits to execute testing.

	$ yeti -s
	Yeti Hub started. LAN: http://10.0.1.10:9000
	                  Local: http://localhost:9000

And, open the http://localhost:9000/ in some web browsers that you like.
Next open new Shell and run test via Yeti command.

	$ yeti tests.html
	  Agent connected: Chrome (23.0.1271.91) / Mac OS
	✓ Testing started on Chrome (23.0.1271.91) / Mac OS
	✓ Agent completed: Chrome (23.0.1271.91) / Mac OS
	✓ 1 tests passed! (0.21 seconds)

That's all. If there is some browsers you want to test, you simply open the
Yeti Hub URL. You can be a very large number of tests on actual browsers via
one command. And Yeti also supports more other testing frameworks such as
[Mocha][mocha], [Jasmine][jasmine], [YUI Test][yuitest].

Yeti is a open source project that has very active releases, please check it.

[qunit]: http://qunitjs.com/
[yeti]: http://yeti.cx/
[mocha]: http://visionmedia.github.com/mocha/
[jasmine]: http://pivotal.github.com/jasmine/
[yuitest]: http://yuilibrary.com/yui/docs/test/
