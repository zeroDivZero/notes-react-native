# `useReducer`

```js
const [state, dispatch] = useReducer(reducer, initialArg, init);
```

Alternative to `useState`. Accepts reducer of type `(state, action) => newState`, and returns current state paired with dispatch method.

Preferred to `useState` when state logic complex, involving multiple sub-values or when next state depends on previous one. Also allows optimizing performance for components that trigger deep updates by passing `dispatch` down instead of callbacks.

```js
const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <>
      Count: {state.count}
      <button onClick={ () => dispatch({ type: 'decrement' }) }>-</button>
      <button onClick={ () => dispatch({ type: 'increment' }) }>+</button>
    </>
  );
}
```
