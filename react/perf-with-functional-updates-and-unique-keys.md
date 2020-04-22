You can cut unecessary re-renders with functional updates and unique element keys.

## Functional Components
When you pass in a function to `useState` or `setState` to refernec the previous state and compute the new state.

```javascript
// w/o functional updates
// "comments" is new every time

const handleClick = useCallback(id => {
  setComments(comments.filter(c => c.id !== id));
}, [comments]);


// w/ functional updates
// "comments" is pointing to the last state before computing the new one.
// so now you only re-render if "comments" changed

const handleClick = useCallback(id => {
  setComments(comments => comments.filter(c => c.id !== id)); // note we're passing the last known "comments" state as a param
}, []);

```

https://reactjs.org/docs/hooks-reference.html#functional-updates


## Unique keys
React uses they `key` attribute to determine which children keys have changed; if it has a new key it hasn't seen before, it'll re-render it.

So if you had something like this:
```javascript
{comments.map((comment, index) => {
  return <Comment {...comment} key={index} onClick={handleClick} />;
})}
```
Every time you modify array "comments", every index in the array is changed, causing all the keys to change as well.


To solve this, you need to give "key" a unique value - in this case `comment.id`.

```javascript
{comments.map(comment => {
  return <Comment {...comment} key={comment.id} onClick={handleClick} />;
})}
```
https://reactjs.org/docs/reconciliation.html#keys


https://staleclosures.dev/preventing-list-rerenders/
