# gobble-es6-transpiler

Compile ES6 files with gobble and [es6-transpiler](https://github.com/termi/es6-transpiler).

## Installation

First, you need to have gobble installed - see the [gobble readme](https://github.com/gobblejs/gobble) for details. Then,

```bash
npm i -D gobble-es6-transpiler
```

## Usage

**gobblefile.js**

```js
var gobble = require( 'gobble' );
module.exports = gobble( 'js' ).map( 'es6-transpiler', options );
```

The `options` argument is optional, and is passed to es6-transpiler (the `src` property is added). See [the full list of options](https://github.com/termi/es6-transpiler#options).

## Source code

```js
module.exports = es6transpiler;

function es6transpiler ( code, options ) {
	var transpiled;

	options.src = code;
	transpiled = require( 'es6-transpiler' ).run( options );

	if ( transpiled.errors.length ) {
		throw new Error( 'Errors transpiling code: ' + JSON.stringify( transpiled.errors ) );
	}

	return transpiled.src;
}

es6transpiler.defaults = {
	accept: '.js'
};
```


## License

MIT. Copyright 2014 Rich Harris
