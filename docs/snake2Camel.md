### Convert snake_case to camelCase

`snake2Camel('rose_are_red') // => rosesAreRed`

```js
const snake2Camel = (str) => {
   return str.replace(/(\_\w)/g, function(k) {
        return k[1].toUpperCase();
    });
}
```
#### Tags

`string` `camel-case` `snake-case` `conversion`

