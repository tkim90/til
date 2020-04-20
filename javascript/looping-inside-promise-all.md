# You can perform operations inside a Promise.all() function

If you're trying to make an API call to each element in an array, you can do so concisely inside `Promise.all()`:

```javascript
  let employees = [...] // an array of objects that you'll use for your API calls

  Promise.all(
    employees.map(async employee => {
      let employeeJobInfo = await getEmployeeJobById(employee.employeeNumber);
      return employeeJobInfo;
    })
  )
```

The result of `Promise.all()` is an array of all requested data.
