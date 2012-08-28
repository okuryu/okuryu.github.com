---
layout: post
title: Building YUI module with shifter
description: How to build your YUI module with new build tool called shifter.
---

YUI Builder tool that has been used to build the module for YUI until now.
This is a tool that can be used as well as YUI core module, in the same
manner if you have own YUI module or YUI Gallery module. YUI Builder works
with Ant (Java), and it can define the information and settings to build
each module. In addition, a convenient macro has been defined by default in
YUI Builder, and through JSLint, and compressed with YUI Compressor, and
build JavaScript code for debugging, you can build them by one command
("ant all"). It is useful Ant because flexibly combine various settings,
but there are no very fast in practice (it took about 10 minutes when I try
to build all YUI core modules on my Mac). It has been increasing more and
more core modules of YUI, YUI was one of the challenges of the time it
takes to build.

Currently, Dav from YUI team working on a new tool called shifter for build
YUI module. Node.js based command line tools, shifter is the future of the
YUI module is likely to use the shifter (the transition to the shifter has
already begun even YUI core modules). I would like to introduce to shifter
can be migrated easily from YUI Builder existing modules.

shifter is since the npm package, you can install that via npm command.

	$ npm install -g shifter

I think the case of an existing YUI module, YUI Builder and configuration
files are named "\*.properties". If this file exists, shifter will switch
to the new build system to generate a "build.json" from this file
automatically. If there is a "build.json", shifter referring to prioritize
the "build.json". In other words, it is you only need to remove the
"build.json" if you want to re-create the "build.json" from "\*.properties".

Future, if you create a new YUI module looks like this.

	$ mkdir -p my-module/src/module-foo/js
	$ cd my-module/src/module-foo
	$ touch my-module/src/module-foo/js/foo.js
	$ touch my-module/src/module-foo/build.json

"build.json" smallest is as follows.

	{
	  "name": "module-foo",
	  "builds": {
	    "foo": {
	      "jsfiles": [
	        "js/foo.js"
	      ]
	    }
	  }
	}

Run shifter command.

	$ shifter
	shifter [info] revving up
	shifter [info] looking for build.json file
	shifter [info] found build.json file, shifting
	shifter [info] putting the hammer down, let's build this thing!
	shifter [info] putting the hammer down
	shifter [info] shifting into gear for my-module
	shifter [info] using preferred jslint setting
	shifter [queu] writing RAW file
	shifter [queu] compressing
	shifter [queu] writing -min file
	shifter [info] shifting for coverage
	shifter [queu] coverage file read, starting coverage
	shifter [queu] writing coverage file
	shifter [info] done racing, the gears are toast
	shifter [info] finished in 1.259 seconds, pretty fast huh?

This completes the build is successful when you run shifter command.
JavaScript file is being output to the directory for the build if build
is successful.

	$ ls -l ../../build/my-module
	total 32
	-rw-r--r--  1 okuryu  staff  1330 Aug 27 23:12 my-module-coverage.js
	-rw-r--r--  1 okuryu  staff    84 Aug 27 23:12 my-module-debug.js
	-rw-r--r--  1 okuryu  staff    52 Aug 27 23:12 my-module-min.js
	-rw-r--r--  1 okuryu  staff    84 Aug 27 23:12 my-module.js

In addition to the features of the YUI Builder, shifter has some useful
features. That is what is on and that the lint feature by default, through
JSLint against JavaScript files in the build process of the shifter. It is
divided into modules that actual yui-lint. They will monitor changes in the
file and run the shifter with a "--watch" option also, it will be me also
through lint build runs automatically every time you save the file.

For more infomation about shifter, look [Dav's post on YUI Blog][yuiblog]
and [shifter user guide][shifter]. I think the shifter will still be
improved in the future, please try to file a ticket on [GitHub][github] if there is
a bug and requests.

[yuiblog]: http://www.yuiblog.com/blog/2012/08/27/shifter-fast-yui-module-building/
[shifter]: http://davglass.github.com/shifter/
[github]: https://github.com/davglass/shifter
