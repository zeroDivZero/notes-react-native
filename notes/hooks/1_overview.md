# OVERVIEW

Functions to "hook into" state and lifecycle of function components. Don't work inside classes. Allow using RN without classes.

Some built-in (like `useState`, `useEffect`), can create own to reuse stateful behavior between components.

## Rules

* Only call hooks at top level, not inside loops, conditions, or nested functions.
* Only call hooks from function components, not regular JS functions.

[Linter plugin](https://www.npmjs.com/package/eslint-plugin-react-hooks) to enforce rules.

## Build Own Hook

To reuse stateful logic between components. Traditional solutions: higher-order components and render props. Custom hook doesn't need additional components to tree.

Extract logic into custom hook:

```js
import React, { useState, useEffect } from 'react';

function useFriendStatus(friendID) {
  const [isOnline, setIsOnline] = useState(null);

  function handleStatusChange(status) {
    setIsOnline(status.isOnline);
  }

  useEffect(() => {
    ChatAPI.subscribeToFriendStatus(friendID, handleStatusChange);
    return () => {
      ChatAPI.unsubscribeFromFriendStatus(friendID, handleStatusChange);
    };
  });

  return isOnline;
}
```

Can be used in different components:

```js
// one component
function FriendStatus(props) {
  const isOnline = useFriendStatus(props.friend.id);

  if (isOnline === null) {
    return 'Loading...';
  }
  return isOnline ? 'Online' : 'Offline';
}

// another component
function FriendListItem(props) {
  const isOnline = useFriendStatus(props.friend.id);

  return (
    <li style={{ color: isOnline ? 'green' : 'black' }}>
      {props.friend.name}
    </li>
  );
}
```

Hooks allow reusing stateful logic, not state itself. Each call to hook has isolated state, can use same custom hook more than once in same component.

Custom hook is convention than feature. If function's name starts with `use` and calls other hooks, it's custom hook. Convention used by linter plugin.
