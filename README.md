## Jump to

* [Overview](#overview)
* [Usage](#usage)
* [Installation](#installation)
* [Links](#links)
* [License](#license)

## Overview 
[[jump to TOC](#jump-to)]

Transforms lodash function imports into sub-modules imports, which allows for a tree-shaking.

It transforms from:

```js
import { debounce } from 'lodash';
```
to:
```js
import debounce from 'lodash/debounce';
```

before the source code is being taken through the typescript compiler.

This way webpack 2 will be able to only include the code that's being actually used.

## Installation
[[jump to TOC](#jump-to)]

1. Install the package:  
```sh
$ npm install lodash-ts-webpack-plugin --save-dev
```

## Usage
[[jump to TOC](#jump-to)]

In your `webpack.config.js` add the `lodash-ts-webpack-plugin` preloader:

```js
// ...
module: {
    rules: [
        {
            test: /\.ts$/,
            loader: 'lodash-ts-webpack-plugin',
            exclude: /node_modules/,
            enforce: 'pre'
        },
        // ...
    ],
    // ...
}
// ...
```

Now somewhere in your `main.ts` typescript file add an ES6 import for lodash:

```js
import { debounce } from 'lodash';
// make sure you have this line as well otherwise you're not using the import member
// and the lodash code will not be included in the bundle
console.log(debounce); 
```

run webpack bundling and check your bundle size.

Update the code to:

```js
import { debounce, zip } from 'lodash';
// make sure you have this lines as well otherwise you're not using the import members
// and the lodash code will not be included in the bundle
console.log(debounce); 
console.log(zip); 
```

run webpack bundling and check your bundle size.  
This time the bundle size should be larger.

## Links 
[[jump to TOC](#jump-to)]

NPM:  
[https://www.npmjs.com/package/lodash-ts-webpack-plugin](https://www.npmjs.com/package/lodash-ts-webpack-plugin)  
GITHUB:  
[https://github.com/efidiles/lodash-ts-webpack-plugin.git](https://github.com/efidiles/lodash-ts-webpack-plugin.git)  

## Author 
[[jump to TOC](#jump-to)]

**Eduard Fidiles**

* [github/efidiles](https://github.com/efidiles)  
* [twitter/efidiles](http://twitter.com/efidiles)  

## License 
[[jump to TOC](#jump-to)]  
Released under the [MIT license](https://github.com/lodash-ts-webpack-plugin/lodash-ts-webpack-plugin/blob/master/LICENSE).


Copyright © 2017, [Eduard Fidiles](https://github.com/efidiles), [Ivan Pankratov](https://github.com/impankratov)