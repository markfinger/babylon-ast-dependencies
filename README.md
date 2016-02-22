# babylon-ast-dependencies

Inspects Babylon ASTs for dependency identifiers


## Install

`npm install --save babylon-ast-dependencies`


## Example

```js
import * as babylon from 'babylon'
import babylonAstDependencies from 'babylon-ast-dependencies';

const ast = babylon.parse(
  `
    import foo from "foo";
    require('./bar')
    export * from './woz'
  `,
  {sourceType: 'module'}
);

const deps = babylonAstDependencies(ast);

console.log(deps.map(dep => dep.source);
// ['foo', './bar', 'woz']
```


## Notes

Lists of objects are returned, where each object has the value
of the identifier as a `source` prop. Rather than simply returning
lists of strings, we use objects as it leaves open the potential
for more contextual information to be provided in a
backwards-compatible manner.
