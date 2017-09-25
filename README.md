# es-module-example-mjs
ES module (.mjs) that can be used natively from node 8.5.0+, without transpilers.

Starting with version 8.5.0, Node.js supports ES modules natively, behind a command line option. Read more at [2ality - Using ES modules natively in Node.js](http://2ality.com/2017/09/native-esm-node.html).

## How this works

To publish a native ES module, simply define `main` [in `package.json`](https://github.com/dandv/es-module-example-mjs/blob/master/package.json#L5) to point to a file with the `.mjs` extension:

```json
{
  "name": "mjs-example",
  "version": "1.0.0",
  "description": "ES native module (.mjs) - requires node 8.5.0+",
  "main": "example.mjs"
}
```

That's the only change. Your [existing transpilation process](https://github.com/dandv/local-iso-dt/blob/master/package.json#L13) to support older Node versions will work as before - just make sure to point Babel to the `.mjs` file(s).

## Usage

1. Install the module:

```bash
yarn add mjs-example
# or, npm install mjs-example
```

2. Create a [test file](https://github.com/dandv/es-module-example-mjs/blob/master/mjs-test.mjs):

```js
import {hello} from 'mjs-example';
console.log(hello);
```

3. Run `node` (v8.5.0+) with the `--experimental-modules` flag:

```bash
node --experimental-modules mjs-test.mjs
```
