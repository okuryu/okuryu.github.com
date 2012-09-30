---
layout: post
title: Testing JavaScript with PhantomJS and YUI Test
description: Headless browser testing your JavaScript with PhantomJS and YUI Test by using Grover
---

There are a variety of what is called a JavaScript test framework,
[YUI Test][yuitest] is one of them. Also, [PhantomJS][phantomjs] is famous as
headless browser, the JavaScript code by using the PhantomJS you can be run
from the command line. If you install PhantomJS the application of this becomes
possible to test JavaScript code on the server. [Grover][grover] is a tool to
run test cases of YUI Test on PhantomJS.

### Install Grover

You can easily install it via npm command since Grover are a matched package
npm.

	npm install -g grover

Must be installed PhantomJS. [Download it][phantomjs-download], they are
provided for binary Mac OS X and Windows, Linux.

### Create test case for YUI Test

YUI Test supports many features, write a simple test case as test.html.

	<script src="http://yui.yahooapis.com/3.7.2/build/yui/yui-min.js"></script>
	<script>
	YUI().use('test', function (Y) {
	  var testCase = new Y.Test.Case({
	    name: 'My Test Case',
	    test1: function () {
	      Y.Assert.areEqual(10, 10);
	    },
	    test2: function () {
	      Y.Assert.isArray([1, 2, 3]);
	    }
	  });
	  Y.Test.Runner.add(testCase);
	  Y.Test.Runner.run();
	});
	</script>

### Run Grover

The test is performed on PhantomjS, results will be display simply by running Grover.

	$ grover test.html
	Starting Grover on 1 files with PhantomJS@1.7.0
	  Running 15 concurrent tests at a time.
	✔ [testSuite_yui_3_7_2_1_1348986046983_9]: Passed: 2 Failed: 0 Total: 2 (ignored 0)
	----------------------------------------------------------------
	✔ [Total]: Passed: 2 Failed: 0 Total: 2 (ignored 0)
	  [Timer] 3.265 seconds

### More advantage

This is the simplest example of YUI Test and Grover. Since there are many more
features, please look at the document.

* [Grover][grover]
* [YUI Test][yuitest]
* [PhantomJS][phantomjs]

[grover]: https://github.com/davglass/grover
[phantomjs]: http://phantomjs.org/
[phantomjs-download]: http://phantomjs.org/download.html
[yuitest]: http://yuilibrary.com/yui/docs/test/
