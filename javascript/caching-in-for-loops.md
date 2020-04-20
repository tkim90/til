# Caching in basic for-loops in HTMLCollections

(from Javascript Patterns)

Looping through HTML collections are expensive because you are looping through DOMs. DOM operations are expensive in general.

## When you're just accessing the HTMLCollection
```javascript
for (let i = 0, max = myarray.length; i < max; i++) {
  // do something with myarray[i]
}
```

Here you cache array `length` to a variable instead of resetting it at every iteration.
