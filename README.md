# Mapsome [![License][LicenseIMGURL]][LicenseURL] [![NPM version][NPMIMGURL]][NPMURL] [![Dependency Status][DependencyStatusIMGURL]][DependencyStatusURL] [![Build Status][BuildStatusIMGURL]][BuildStatusURL]

Find maped element of an array that will satisfy condition of some.

[Map][mapURL] + [Some][someURL] + `early return of an element`

## Install

```
npm i mapsome --save
```

## How come?

Lets look at regular `map-filter` example:

```js
const map = (a) => ++a;
const condition = (a) => a > 2;

[1, 2, 3, 4]
    .map(map)           /* loop full array */
    .filter(condition)  /* loop full array again */
    .pop();             /* get value */
// returns
3
```

With `mapsome` this would look this way:

```js
const map = (a) => ++a;
const condition = (a) => a > 2;

mapsome(map, condition, [1, 2, 3, 4]);
// returns
3
```

`mapsome` works much faster because no need map full array, first satisfied condition will break the loop.

## API
### mapsome(map [, condition ], array)
- mapping function
- condition of stopping the loop
- array

`mapsome` could be used with `map` function only:

```js
const map = (a) => ++a;
mapsome(map, [0, 0, 3, 0]);
// returns
3

// same as
mapsome(map, a => a, [0, 0, 3, 0]);
// returns
3
```
## Environments

### Node.js

In old `node.js` environments that supports `es5` only, `mapsome` could be used with:

```js
var mapsome = require('mapsome/legacy');
```

### Web Browser

`mapsome` could be installed via `bower` with:

```sh
bower install mapsome --save
```

When loaded in browser `mapsome` uses global variable with same name (when `browserify` or `webpack` did not used).

## License

MIT

[NPMIMGURL]:                https://img.shields.io/npm/v/mapsome.svg?style=flat
[BuildStatusIMGURL]:        https://img.shields.io/travis/coderaiser/mapsome/master.svg?style=flat
[DependencyStatusIMGURL]:   https://img.shields.io/gemnasium/coderaiser/mapsome.svg?style=flat
[LicenseIMGURL]:            https://img.shields.io/badge/license-MIT-317BF9.svg?style=flat
[NPMURL]:                   https://npmjs.org/package/mapsome "npm"
[BuildStatusURL]:           https://travis-ci.org/coderaiser/mapsome  "Build Status"
[DependencyStatusURL]:      https://gemnasium.com/coderaiser/mapsome "Dependency Status"
[LicenseURL]:               https://tldrlegal.com/license/mit-license "MIT License"

[someURL]:                  https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some
[mapURL]:                   https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map

