Opentip
=======

[Opentip][opentip] is a free opensource Java-Script tooltip class.


Features
--------

It supports:

- Stems (little pointers)
- Automatic content download with [AJAX][ajax]
- Different styles
- Automatic repositioning of the tooltip if it's not in the viewport of the browser anymore
- All kind of triggers (The tooltip can be triggered by mouse over, click, form submit,... everything you can think of really)
- CSS3 Animations
- Well tested, with over 200 unit tests

As of Version 2.0 Opentip does **no longer depend on [Prototype]**. You can choose
*any* adapter you want so you can work with the framework of your choice.

Supported frameworks are:

- Native. You can use this one if you don't use any framework.
- [Ender]
- [jQuery]
- [Prototype]


> If you want to contribute, please read on in the [contribute](#contribute)
> section. If you are migrating from version **1.x** please refer to the
> [migration section](#migrating-from-opentip-1x-to-2x)

Installation
------------

### Component

The easiest and recommended way to install *opentip* is with [component]. Just
add `enyo/opentip` as dependency in your `component.json` and rebuild it.

Simply requiring opentip then activates the tooltips: `require "opentip";`


### Ender

If you prefer [ender] as package manager just install it like this:

```bash
$ ender build opentip
```

### Other

If you don't use component or ender, just download `lib/opentip.js` and
`lib/adapter.FRAMEWORK.js` and include them in this order.

* * *

You should include opentip's CSS as well. It's in `css/opentip.css`. (Except
for [component] of course which automatically bundles the css.)

Usage
-----

*Version 2.0.0-dev*

With HTML data attributes:

```html
<div data-ot="Tooltip content" data-ot-show-on="click">Click me</div>
```

or with the Javascript API:

```js
$('elementId').opentip('Content', { showOn: "click", ...options... });
```

For the complete documentation please visit [www.opentip.org][opentip].


Future plans
------------

- ~~Become library independant. I'm currently working on
  extracting all prototype functionality, so I can switch library easily. The
  next library   I'll support will be jquery, and then mootools.~~

- Add more skins.

- Add cooler loading animation.

- ~~Implement unit tests.~~


If you have ideas, please contact me!


Contribute
----------

The latest stable version is always in the **[master](https://github.com/enyo/opentip)** branch (which always
points at the latest version tag).

The latest development version is in the **[develop](https://github.com/enyo/opentip/tree/develop)** branch.

> Use the develop branch if you want to contribute or test features.

Please do also **send pull requests to the `develop` branch**.

### Coffeescript

Opentip is written in [Coffeescript](http://coffeescript.org) so *do not* make
changes in the Javascript files. **I will not merge requests written in Javascript.**

### Node

To start the test environment [install node](http://nodejs.org) first if you haven't done so already.

Then go into the `test/` directory and install all dependencies. (You only have
to do this the first time):

```bash
$ cd test/
$ npm install
```

And you're ready to launch the server:

```bash
$ ./server.js
```

Now simply visit `http://localhost:3000` in your browser to see the tests.

It should look like this:

![Tests screenshot](https://raw.github.com/enyo/opentip/develop/files/tests.png)

All tests are located in `assets/js/tests/` and are written in coffeescript but
compiled on the fly.

The webserver also automatically compiles any opentip changes (as well as the
adapter changes), so don't worry about compiling coffeescript. When the time comes
to deploy everything, I'll take care of properly bundling all Javascript files.

If you add a change, please make sure that all tests pass!


### Cake

To compile and bundle the library use `cake`.

Just type the command without any arguments `$ cake` in the source directory to list all commands available.

To compile all source files:

```bash
$ cd path/to/opentip-source 
$ cake build
```

> You don't have to do this if you simply want me to merge a change. The test
> webserver compiles on the fly, and I only build and bundle the files before
> I release a new version.


Migrating from Opentip 1.x to 2.x
---------------------------------

Those are the major changes you should look out for when migrating from 1.x to 2.x:

- There's no `Tip` or `Tips` object anymore. Everything is done through
  `Opentip`

- The recommend way to create opentips now is to call
  `new Opentip(element, content, title, options)`, or with the framework of
  your choice (eg, [ender]: `$("#my-div").opentip(content, title options)`)

- The instantiation of new tips inside an event (eg: `onclick`, `onmouseover`)
  is no   longer supported! This would create new opentips everytime the event
  is fired.

- `Opentip.debugging = true;` does no longer exist. Use `Opentip.debug = true;`

- Positions are no longer of the weird form `[ "left", "top" ]` but simply
  strings   like `"top left"` or `"right"`

- `stem.size` has been dropped in favor of `stem.length` and `stem.base`

- Most of the design is now done in JS since the whole thing is a canvas now.

- The way close buttons are defined has completely changed. Please refer to the
  docs for more information.

Tagging
-------

Tagging in this project is done with my [tag script](http://github.com/enyo/tag).


Authors
-------

Opentip is written by Matias Meno.<br>
Website design by Tjandra Mayerhold.

### Contributors

Thanks to the following people for providing bug reports, feature requests and fixes:

- Torsten Saam
- Aaron Peckham
- Oguri
- MaxKirillov
- Nick Daugherty

If I forgot somebody, please just tell me.

### Related projects

You might also be interested in my [formwatcher](http://www.formwatcher.org/) or
[dropzone](http://www.dropzonejs.com/).

License
-------
(The MIT License)

Copyright (c) 2012 Matias Meno &lt;m@tias.me&gt;<br>

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[opentip]: http://www.opentip.org/
[prototype]: http://www.prototypejs.org/
[jquery]: http://jquery.com/
[ajax]: http://en.wikipedia.org/wiki/Ajax_(programming)
[excanvas]: https://github.com/enyo/excanvas
[ender]: http://ender.no.de
[component]: https://github.com/component