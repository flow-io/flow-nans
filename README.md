flow-nans
=========

Through stream which removes all non-numeric values from a stream.


## Installation

``` bash
$ npm install flow-nans
```


## Examples

``` javascript
var eventStream = require( 'event-stream' ),
	fStream = require( 'flow-nans' );

var data = new Array( 9 );

// Create some data...
data[ 0 ] = 'a';
data[ 1 ] = true;
data[ 2 ] = function(){};
data[ 3 ] = {};
data[ 4 ] = [];
data[ 5 ] = undefined;
data[ 6 ] = NaN;
data[ 7 ] = null;
data[ 8 ] = 0;

// Create a readable stream:
var readStream = eventStream.readArray( data );

// Create a new NaN filter stream:
var stream = fStream()
	.accessors( 'd', function ( d ) {
		return d;
	})
	.stream();

// Create the pipeline:
readStream.pipe( stream )
	.pipe( eventStream.stringify() )
	.pipe( process.stdout );
```

## Tests

Unit tests use the [Mocha](http://visionmedia.github.io/mocha) test framework with [Chai](http://chaijs.com) assertions.

Assuming you have installed Mocha, execute the following command in the top-level application directory to run the tests:

``` bash
$ mocha
```

All new feature development should have corresponding unit tests to validate correct functionality.


## License

[MIT license](http://opensource.org/licenses/MIT). 


---
## Copyright

Copyright &copy; 2014. Athan Reines.

