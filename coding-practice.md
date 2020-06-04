

## basic





- Short string manupilation





### build in methods usages

### `String`:

`substring`, `indexOf`, `lastIndexOf`

> between-markers

`capital`



```javascript
function maxDigit(target: number): number {
  let numArr = target
    .toString()
    .split("")
    .map((numStr) => parseInt(numStr));
  return Math.max(...numArr);
}
```



[Count Digits"](https://js.checkio.org/mission/count-digits/)

```js
// Mine 
function countDigits(text: string): number {
  return text
    .split("")
    .map((char) => +Number.isInteger(parseInt(char)))
    .reduce((acc, cur) => acc + cur, 0);
}
```

```javascript
const realSolution = (text: string): number => text.match(/\d/g)?.length || 0
```

```
	return [...text].filter(e=> !isNaN(parseInt(e))).length;
```

