# When using the .then .catch pattern, fetch() only enters the catch(error) code if there is a network problem, not if the API responds a with a failed status code.

```javascript
 fetch("http://httpstat.us/500")
    .then(function() {
        console.log("ok");
    }).catch(function() {
        console.log("error");
    });
``` 

Actually returns "ok". 🤯

This is because fetch only catches errors for network errors. To fix this, fetch provides a `.ok` method to verify if the API response is within the range of successful status codes.

```javascript
fetch("http://httpstat.us/500")
    .then(function(response) {
        if (!response.ok) {
            throw Error(response.statusText);
        }
        return response;
    }).then(function(response) {
        console.log("ok");
    }).catch(function(error) {
        console.log(error);
    });
``` 

You can improve this with a generic error handler:

```javascript
function handleErrors(response) {
    if (!response.ok) {
        throw Error(response.statusText);
    }
    return response;
}

fetch("http://httpstat.us/500")
    .then(handleErrors)
    .then(function(response) {
        console.log("ok");
    }).catch(function(error) {
        console.log(error);
    });
```


Source: https://www.tjvantoll.com/2015/09/13/fetch-and-errors/
