### A `controlled input` is a coding pattern in react where you have complete control over the input's state, value, and `onChange` events.

#### Why?
It's good practice to use controlled components because React can keep these values in state, in a single source of truth. We _control_ what happens to the form's value and how it changes.

React docs[0]:

> In HTML, form elements such as `input`, `textarea`, and `select` typically maintain their own state and update it based on user input. In React, mutable state is typically kept in the state property of components, and only updated with setState().

[0]https://reactjs.org/docs/forms.html#controlled-components

---

Class

```javascript
constructor() {
  super();
  this.state = {
    search: '',
  }
}

onChangeHandler(event) {
  this.setState({ search: event.target.value });
}

render () {
  <input 
    type='text'
    onChange={this.onChangeHandler.bind(this)}
  />
}
```

Hooks
```javascript
const [inputValue, setInputValue] = useState('');

// target is the `input` element, `value` is its contents
const onChangeHandler = event => {
  setInputValue(event.target.value);
}

<input
  type='text'
  value={inputValue}
  onChange={onChangeHandler}
/>
``` 


Controlled input
```html
<input type='text' value='Hello'/>
```

Not a controlled input
```html
<input type='text' />
```
