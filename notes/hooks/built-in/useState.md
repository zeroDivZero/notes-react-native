# `useState`

```js
const [state, setState] = useState(initialState);
```

Returns stateful value and function to update it. State doesn't have to be object; preserved between re-renders.

```js
import React, { useState } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={ () => setCount(count + 1) }>
        Click me
      </button>
    </div>
  );
}
```

Can use multiple times in same component:

```js
const [age, setAge] = useState(42);
const [fruit, setFruit] = useState('banana');
const [todos, setTodos] = useState([{ text: 'Learn Hooks' }]);
```

Array destructuring allows custom state name (not part of `useState` API).

`setState` function enqueues re-render of component.
