# broccoli-yuidoc

This plugin provides support for generating YUIDoc via a broccoli
pipeline.

## Installation

```
npm install --save-dev broccoli-yuidoc
```

## Configuration

Additional options related to YUIDoc may be may be passed as an object
`yuidoc` to `yuidocCompiler`. 
All of the available options can be found on [YUIDoc's official documentation
page](https://yui.github.io/yuidoc/args/index.html).

Note: If a `yuidoc.json` file exists in a parent directory, it will be 
used as well.

## Usage

```js
var yuidocCompiler = require('broccoli-yuidoc');
var mergeTrees = require('broccoli-merge-trees');

// As with most other broccoli plugins, you can
// define the base directory of the files you
// would like documentation generated for as 
// the first paramter, and specify source and
// destination directories.
// Custom YUIdoc options is passed as yuidoc.
var yuidocTree = yuidocCompiler('app', {
	srcDir: '/',
	destDir: 'docs',
	yuidoc: {
		// .. yuidoc option overrides
	}
});


// To merge the YUIdoc build tree with, let's say,
// an ember application tree, use broccoli-mergetrees 
var applicationTree = mergeTrees([app.toTree(), yuidocTree]);

module.exports = applicationTree;
```

It's recomended to use `broccoli-merge-trees` to finally produce
a signle tree for broccoli to work on.
