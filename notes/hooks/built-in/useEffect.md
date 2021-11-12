# `useEffect`

```js
useEffect(didUpdate);
```

Accepts function that contains imperative, possibly effectful code, executed after render committed to screen (changes flushed to DOM).

Mutations, subscriptions, timers, logging, and other side effects not allowed inside main body of function component (render phase); leads to bugs and inconsistencies in UI.

Use `useEffect`. Passed-in function by default runs after every render, including first. Escape hatch from purely functional world into imperative world.

Serves same purpose as `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` in React class.

```js
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `You clicked ${count} times`;
  });

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

Can optionally specify "clean up" function:

```js
import React, { useState, useEffect } from 'react';

function FriendStatus(props) {
  const [isOnline, setIsOnline] = useState(null);

  function handleStatusChange(status) {
    setIsOnline(status.isOnline);
  }

  useEffect(() => {
    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
    // unsubscribe when component unmounts or re-renders
    return () => {
      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
    };
  });

  if (isOnline === null) {
    return 'Loading...';
  }
  return isOnline ? 'Online' : 'Offline';
}
```

Applying effect or cleaning up after every render may create perf problem. Skip if specified values don't change between renders.

```js
useEffect(() => {
  document.title = `You clicked ${count} times`;
}, [count]); // only re-run effect if count changes
```

Can use multiple effects in same component.
