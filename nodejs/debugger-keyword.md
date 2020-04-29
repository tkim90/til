# The `debugger` keyword will 'pause' the script in nodejs where you can inspect the objects in async code

For example, if you're doing an API call and want to see the result, throw in a `debugger` statement to inspect it.
In VSCode, you can hit `F5` to run the script with the debugger.

Example:
```javascript
const request = require('request-promise');

const getData = async function() {
  const json = await request({
    url: URL,
    json: true
  });
}

(async function() {
  try {
    await getData()
  } catch(e) {
    console.log('Error', e);
  }

  debugger;
})();
```
