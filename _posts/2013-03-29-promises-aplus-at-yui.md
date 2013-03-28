---
layout: post
title: Promises/A+ at YUI
description: Added a module that compatible with the Promises/A+ in YUI 3.9.0, which was released recently.
---

Added a module that compatible with the [Promises/A+][promises-aplus] in
[YUI 3.9.0][yui390], which was released recently. Promises/A+ is a
specification that further improve the specification of
[Promises/A][promises-a] of CommonJS. Such as specifications and test cases
that have been published on GitHub. Today, I would like to introduce the
sample code for that module.

### Load promise module

First, you need to load `promise` module, and you can use `Y.Promise` within
YUI sandbox.

{% highlight javascript %}
YUI().use('promise', function (Y) {

    // You can use Y.Promise

});
{% endhighlight %}

### "Y.Promise" and "then" function

Basic usage is something similar to the following.

{% highlight javascript %}
var promise = new Y.Promise(function (fulfill) {
    fulfill(10);
});

promise.then(function (value) {
    Y.log(value); // value: 10
});
{% endhighlight %}

The callback function of `Y.Promise` accept a second function for rejected.

{% highlight javascript %}
var promise = new Y.Promise(function (fulfill, reject) {
    reject(20);
});

promise.then(function (value) {
    Y.log(value);
}, function (value) {
    Y.log(value); // value: 20
});
{% endhighlight %}

A instance of `Y.Promise` is chainable.

{% highlight javascript %}
var promise = new Y.Promise(function (fulfill, reject) {
    Y.log('OK 1');
    fulfill(10);
});

promise.then(function (value) {
    Y.log('OK 2');
    return Y.Promise(function (fulfill) {
        fulfill(10);
    });
}).then(function (value) {
    Y.log('OK 3');
});
{% endhighlight %}

This result just below.

	OK 1
	OK 2
	OK 3

### "Y.when" function and "Y.batch" function

The promise module provide 2 advance functions for YUI instance.

`Y.when` function is abstraction API allowing you to interact with promises
or raw values as if they were promises.

{% highlight javascript %}
Y.when(new Y.Promise(function(fulfill) {
    fulfill(10);
}), function (value) {
    Y.log(value); // value: 10
});
{% endhighlight %}

`Y.batch` function returns a new promise that will be resolved when all
operations have completed.

{% highlight javascript %}
function fn(value) {
    return new Y.Promise(function (fulfill, reject) {
        fulfill(value);
    });
}

Y.batch(fn(10), fn(20), fn(30)).then(function (result) {
    Y.log(result); // [10, 20, 30]
});
{% endhighlight %}

So please try using it now.

[yui390]: http://www.yuiblog.com/blog/2013/03/13/announcing-yui-3-9-0/
[promises-a]: http://wiki.commonjs.org/wiki/Promises/A
[promises-aplus]: http://promises-aplus.github.com/promises-spec/
