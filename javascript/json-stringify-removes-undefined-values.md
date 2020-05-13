# JSON.stringify(myObj) removes the keys with undefined values.

```javascript
let obj = { a: undefined, b: 'hi' };
console.log(JSON.stringify(obj))
// returns { b: "hi" } !
```

Luckily, you can override this behavior.

JSON.stringify takes in a `replacer` callback as a second param.
`replacer` takes in two params, the `key` and `value` being stringified.

```javascript
let obj = { a: undefined, b: 'hi' };
const replacer = (key, value) =>
  typeof value === 'undefined' ? null : value;

const stringified = JSON.stringify(user, replacer);
// returns "{\"a\":null,\"b\":\"hi\"}"
```
