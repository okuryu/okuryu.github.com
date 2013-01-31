---
layout: post
title: Faster function that happen async with YUI
description: From next version of YUI, `timers` module will add into YUI core module. You can use `Y.soon` function by this module.
---

From next version of YUI, `timers` module will add into YUI core module. You can
use `Y.soon` function by this module.

This function is similar to `Y.later`, used when there is something that you
want to process asynchronously. Recently, we have come out that can be used to
implement a function called `setImmediate` in IE10 and Node.js 0.9. `Y.soon` can
also consider such implementation, asynchronous processing is performed faster
than `Y.later`.

Just show you an example.

	<script src="http://yui.yahooapis.com/3.9.0pr2/build/yui/yui-min.js"></script>
	<script>
	YUI().use('timers', function (Y) {
	  Y.log('hello timers');
	  var asyncTask = Y.soon(myTask);
	  Y.log('end timers');
	  function myTask() {
	    Y.log('called myTask()');
	  }
	});
	</script>

It results in the following.

	hello timers
	end timers
	called myTask()

YUI also supports Node.js, so that the same logic also works on the browser,
even on Node.js.

In addition, there is a function called to `cancel` in object that `Y.soon`
returns. You can then call this function to cancel the action to be performed.

	<script src="http://yui.yahooapis.com/3.9.0pr2/build/yui/yui-min.js"></script>
	<script>
	YUI().use('timers', function (Y) {
	  Y.log('hello timers');
	  var asyncTask = Y.soon(myTask);
	  Y.log('end timers');
	  asyncTask.cancel();
	  function myTask() {
	    Y.log('called myTask()');
	  }
	});
	</script>

If you call `cancel` and you will not be executed.

	hello timers
	end timers

This feature is available from YUI 3.9.0, its Preview Release 2 is currently.
The GA is planned in the near future. There is a possibility that `Y.later` is
obsolete in the future, it would be good to remember that the `Y.soon`.

