### Text Converesion

#### Validate IP address

`validate('192.168.40.2') // -> true`

```
const validate = (str) => {
    return /^(([1-9]?\d|1\d\d|2[0-4]\d|25[0-5])(\.(?!$)|$)){4}$/.test(str);
};
```


