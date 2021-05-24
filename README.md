# Tree shaker

**Status: complete (hack)**

This might be useful if you’re working with a big library that supports tree-shaking, but can’t keep everything inside of a fancy build system. For instance: if you want to pull bits of [`date-fns`](https://www.npmjs.com/package/date-fns) onto a Webflow project, but don’t want to pull in the whole ~100kb library. This repo was a really quick way for me to do just that.

The project is nothing special, it’s practically just the [Webpack Getting Started](https://webpack.js.org/guides/getting-started/) project with tree-shaking enabled.

## Usage

```sh
git clone git@github.com:rileyjshaw/tree-shaker.git
cd tree-shaker
yarn

# Add and use some libraries. For instance:
yarn add date-fns
echo 'import { formatRelative, subDays } from "date-fns";
import { es, ru } from "date-fns/locale";

var now = new Date();
var before = subDays(now, 3);

console.log(formatRelative(before, now),
	formatRelative(before, now, { locale: es }),
	formatRelative(before, now, { locale: ru }))' >src/index.js

# Then build it, and use the minified bundle however you need to.
yarn build
cat dist/main.js
```
