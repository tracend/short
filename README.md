
# Short [![Build Status](https://secure.travis-ci.org/edwardhotchkiss/short.png)](http://travis-ci.org/edwardhotchkiss/short)

> NodeJS URL Shortener backed by MongooseJS w/ Complete Example Site

### Notes on 0.1.0

  This is a finalized API. Previous API structure is not compatible with short 1.0.0+

### Running Examples

```bash
$ git clone git@github.com:edwardhotchkiss/short.git
$ cd short/examples/basic
$ node API.js
```

### Installation

```bash
$ npm install short
```
***

### Basic API Usage

* Using short within your own project as an API interface

```javascript

/*!
  Core Modules
 */

var short = require('../../lib/short'),
    // URL to Shorten
    URL = 'http://nodejs.org/';

short.connect('mongodb://localhost/short');

short.connection.on('open', function(){
  /* connected to mongodb */
});

short.connection.on('error', function(error){
  throw new Error(error);
});

/*!
  Generate a Shortened URL
  Retrieve URL based on Generated Hash
 */

short.generate(URL, function(error, shortURL) {
  if (error) {
    throw new Error(error);
  } else {
    short.retrieve(shortURL.hash, function(error, shortenedURLObject) {
      if (error) {
        throw new Error(error);
      } else {
        // URL
        console.log('URL:', shortenedURLObject.URL);
        // Base 62 Hash
        console.log('hash:', shortenedURLObject.hash);
        process.exit(0);
      };
    });
  }
});

/* EOF */
```
***

### Connecting (cURL) to the Complete Example

Just add the domain you'd like to the end of localhost:8080/api

```bash
$ curl localhost:8080/api/http://www.longdomain.com/
```

## Pull Requests

  * fork
  * clone
  * improve
  * pull request
  * **instant karma!**

## Run Tests

``` bash
$ npm test
```

## License (MIT)

Copyright (c) 2011, Edward Hotchkiss.

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

### Author: [Edward Hotchkiss][0]
### Contributors: [Kevin][1]

[0]: http://ingklabs.com/
[1]: http://github.com/thinkroth/
