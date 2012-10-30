---
layout: post
title: Node.js in YUI
description: Summarize Node.js based YUI tools.
---

[Article about Node.js][nodejs-yuiblog] that was released for the first time
in [YUI Blog][yuiblog] was that of 2010. Although more than two years has
passed since then, a set of tools around YUI is that it works on all Node.js
finally. I think this time I would like to summarize that also serves as an
introduction to each tool.

### [yUglify][yuglify]

A tool that has been wrapped for YUI based on the [UglifyJS][ugulifyjs] and
[cssmin][cssmin]. YUI Compressor that has been used until now will be
obsolete in the future We will use this as a successor.

### [YUI Test][yuitest]

A JavaScript unit testing framework. It has supported Node.js at a
relatively early stage. Have tested using YUI Test is also YUI core code.

### [Yeti][yeti]

A tool for cross-browser testing. This is a tool that allows you to run a
test with a single command to test on multiple browsers and devices. You can
implement the proprietary protocols, Yeti is inside is an interesting tool
that can be very good. Easy to understand and I would watch the
[Reid's video][reid-yeti] and [Dav's video][dav-yeti].

### [Grover][grover]

It is a tool to run on a headless browser tests of YUI Test using
[PhantomJS][phantomjs]. Please take a look at last month, so I introduced
in [my blog post][grover-blog].

### [YUI Doc][yuidoc]

It is a tool that generates API documentation from the code of JavaScript.
Previously, it had been implemented in Python, Node.js has now become well.

### [Shifter][shifter]

It is a tool used to build YUI module corresponding to the successor of YUI
Builder. YUI Builder was Java(Ant), Shifter is Node.js base. Please take a
look because this is also introduced in [the previous blog][shifter-blog].

### [Yogi][yogi]

This has not been officially announced or still under development, it is
still without much documentation. It seems to be something like a support
tool for the development of gallery modules and YUI.

Because they are all published on [GitHub][yui-github], you can contribute
the code if anyone has signed the [CLA of YUI][yui-cla] everyone.

[nodejs-yuiblog]: http://www.yuiblog.com/blog/2010/04/05/running-yui-3-server-side-with-node-js/
[yuiblog]: http://yuiblog.com/
[yuglify]: https://github.com/yui/yuglify
[ugulifyjs]: https://github.com/mishoo/UglifyJS
[cssmin]: https://github.com/jbleuzen/node-cssmin
[yuitest]: https://github.com/yui/yuitest
[yeti]: http://yeti.cx/
[dav-yeti]: http://www.youtube.com/watch?v=85Q06z7_B0w
[reid-yeti]: http://www.youtube.com/watch?v=tpGBlJ7DBks
[grover]: https://github.com/davglass/grover
[phantomjs]: http://phantomjs.org/
[grover-blog]: http://www.okuryu.com/2012/09/30/testing-javascript-with-phantomjs-and-yui-test.html
[yuidoc]: https://github.com/yui/yuidoc
[shifter]: https://github.com/yui/shifter
[shifter-blog]: http://www.okuryu.com/2012/08/28/building-yui-module-with-shifter.html
[yogi]: https://github.com/yui/yogi
[yui-github]: https://github.com/yui
[yui-cla]: http://yuilibrary.com/contribute/cla/
