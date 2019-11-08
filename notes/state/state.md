# STATE

Track data that change over time. If changes, rerender component (and its children).

For each piece of data, answer 3 questions:

1. What is changing?
2. What type is it?
3. What is its default value?

To add to state, use **hook** `useState` and provide default value:

```javascript
import React, { useState } from 'react';

const [counter, setCounter] = useState(0);

<Button title="Increase" onPress={() => { setCounter(counter + 1); }} />
```

Should not modify state directly. When `setCounter` used, rerender component.

`setCounter` does not update `counter` immediately. Updated briefly after. Component re-rendered with updated value.

This is how state is managed in _functional_ component, which is preferred over class-based component.

State can be passed to child as prop. Generally, create state vars in most parent component that needs to read or change them. If child needs to read, simply pass state as value. If child needs to change, pass down callback.
