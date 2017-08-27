[![Build Status](https://travis-ci.org/kaelzhang/napi-penteract.svg?branch=master)](https://travis-ci.org/kaelzhang/napi-penteract)
[![Coverage](https://codecov.io/gh/kaelzhang/napi-penteract/branch/master/graph/badge.svg)](https://codecov.io/gh/kaelzhang/napi-penteract)
<!-- optional appveyor tst
[![Windows Build Status](https://ci.appveyor.com/api/projects/status/github/kaelzhang/napi-penteract?branch=master&svg=true)](https://ci.appveyor.com/project/kaelzhang/napi-penteract)
-->
<!-- optional npm version
[![NPM version](https://badge.fury.io/js/napi-penteract.svg)](http://badge.fury.io/js/napi-penteract)
-->
<!-- optional npm downloads
[![npm module downloads per month](http://img.shields.io/npm/dm/napi-penteract.svg)](https://www.npmjs.org/package/napi-penteract)
-->
<!-- optional dependency status
[![Dependency Status](https://david-dm.org/kaelzhang/napi-penteract.svg)](https://david-dm.org/kaelzhang/napi-penteract)
-->

# penteract

The node.js wrapper of Tesseract OCR using N-API.

ATTENSION that this package is still Working In Progress, and only support Mac OS X for now.

Contributions are welcome.

## Install

Before install node.js penteract, the following dependencies should be installed

```sh
brew install pkg-config tesseract
```

Then npm install

```sh
$ npm install penteract@latest # the version using nan
$ npm install penteract@n-api  # the version using n-api

```

## Usage

### Recognize an Image Buffer

```js
import {
  recognize
} from 'penteract'

import fs from 'fs-extra'

const filepath = path.join(__dirname, 'test', 'fixtures', 'penteract.jpg')

fs.readFile(filepath).then(recognize).then(console.log)
// 'penteract'
```

### From a Readable Stream

```js
const stream = fs.createReadStream(filepath)
recognize(stream).then(console.log)
```

### Recognize a Local Image File

```js
import {
  fromFile
} from 'penteract'

fromFile(filepath, {lang: 'eng'}).then(console.log)
// 'penteract'
```

## recognize(image [, options])

- **image** `Buffer|Stream.Readable`
- **options** `Object=`
  - **lang** `(String|Array.<String>)=eng` specify language(s) used for OCR. Run `tesseract --list-langs` in command line for all supported languages. Defaults to `'eng'`.

Returns `Promise.<String>`

## fromFileSync(filepath [, options])

- **filepath** `Path`
- **options**

Returns `Promise.<String>` the recognized text.

## License

MIT
