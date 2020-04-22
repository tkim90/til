# JS considers two functions that have the same code to be different

```javascript
const a = () => {}
const b = () => {}
console.log(a === b) // false
```

In the above example, we have two functions that have the same code.

But when we compare them, they don't equal each other. This is because:
- Functions are objects in JS.
- Two objects that "look" the same actually point to different values in memory. This is why it says "false" when comparing them.
   - AKA the code inside `a`'s function points to a different memory than the code inside `b`. So it doesn't matter that they look the same.

Because creatinga new "identical" function can be memory expensive, you could memoize the function.

