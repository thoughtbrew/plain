### Convert camelCase to snake_case

`camel2Snake('rosesAreRed') // => roses_are_red`

```js
const camel2Snake = (str) => {
  return String(str)
    .replace(/([A-Z])/g, function($1){return "_"+$1.toLowerCase();});
}
```
#### Tags

`string` `snake-case` `camel-case` `conversion`

