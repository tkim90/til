You can access the "root element" used to render all React components in `gatsby-browser.js`.

Create a function that takes in the `element`. Wrap all your context providers in this function.

```javascript
// ./src/ gatsby-browser.js

import React, { createContext } from 'react';

const myContext = createContext(null);

const wrapRootElement = ({ element }) => {
  <myContext.Provider>
    {element}
  </myContext.Provider>
}

```
