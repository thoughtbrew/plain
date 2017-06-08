### IP Addresses

#### Convert subnet mask to shorthand

`mask2Short('255.255.255.0') // -> 24`

```
const mask2Short = (netmask) => {
  const mask = (netmask.split('.').map(Number)
      .map(part => (part >>> 0).toString(2))
      .join('')).split('1').length -1;
  return `/${mask}`;
}
```

#### Convert subnet shorthand to mask

`short2Mask('24') // -> 255.255.255.0`

```  
const short2Mask = (bitCount) => {
  const mask = [];
  for (var i = 0; i < 4 ; i++) {
  const n = Math.min(bitCount, 8);
  mask.push(256 - Math.pow(2, 8-n));
  bitCount -= n;
  }
  return mask.join('.');
} 
```
  
