Depending on the browser, localStorage values get converted from boolean to string.

Say you had localStorage.setItem("isAuth", true)...
Firefox will store "isAuth" as boolean `true`.
Chrome will store "isAuth" as _string_ `"true"`

This can get confusing when you're setting it to false:
```javascript
localStorage.setItem("isAuth", false)
localStorage.getItem("isAuth") // returns "false" string!
```

so if you do
`if (localStorage.getItem("isAuth"))`

that's like saying
`if ("false")`

which evaluates to true!

Very confusing.
