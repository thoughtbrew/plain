### Binary search version of Array.indexOf()

`binaryIndexOf([1, 2, 3, 4], 2) // => 1`

```
const binaryIndexOf = (arr, str) => {
    let minIdx = 0;
    let maxIdx = arr.length - 1;
    let currIdx;
    let currEl;
    while (minIdx <= maxIdx) {
        currIdx = (minIdx + maxIdx) / 2 | 0;
        currEl = arr[currIdx];
 
        if (currEl < str) {
            minIdx = currIdx + 1;
        }
        else if (currEl > str) {
            maxIdx = currIdx - 1;
        }
        else {
            return currIdx;
        }
    }
    return -1;
}
```
#### Notes

Array must be sorted.

#### Tags

`array` `indexOf` `binary-search`
