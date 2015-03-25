# deAMDify2

Forked from [deAMDify](https://github.com/jaredhanson/deamdify).

This module is a [browserify](http://browserify.org/) plugin that will transform
[AMD](https://github.com/amdjs) modules into [Node.js](http://nodejs.org/)-style
modules so that they can be included in browser-ified bundles.

With this transform in place, Node and AMD modules can be freely intermixed, and
the resulting bundle can be used without the need for a separate loader such as
[RequireJS](http://requirejs.org/).

## Install

    $ npm install deamdify2

## Usage

#### Command Line

Bundle up all required modules, including AMD modules, into a single file
using `browserify` with the `deamdify2` transform.

    browserify -t deamdify2 main.js -o bundle.js

#### API

```javascript
var browserify = require('browserify');
var fs = require('fs');

var b = browserify('main.js');
b.transform('deamdify2');

b.bundle().pipe(fs.createWriteStream('bundle.js'));
```

#### package.json

For packages that are written as AMD modules, add a browserify transform field
to `package.json` and browserify will apply the transform to all modules in the
package as it builds a bundle.

```
{
  "name": "anchor",
  "main": "main",
  "browserify": {
    "transform": "deamdify2"
  }
}
```

## Tests

    $ npm install
    $ npm test

## Credits

  - [Jared Hanson](http://github.com/jaredhanson)

## License

[The MIT License](http://opensource.org/licenses/MIT)

Copyright (c) 2013 Jared Hanson <[http://jaredhanson.net/](http://jaredhanson.net/)>
Copyright (c) 2015 Jamund Ferguson
