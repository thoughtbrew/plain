
### Convert subnet mask to shorthand

`mask2Short('255.255.255.0') // -> 24`

```
const mask2Short = (netmask) => {
  const mask = (netmask.split('.').map(Number)
      .map(part => (part >>> 0).toString(2))
      .join('')).split('1').length -1;
  return `/${mask}`;
}
```
#### Tags

`string` `subnet-mask` `shorthand` `conversion`

