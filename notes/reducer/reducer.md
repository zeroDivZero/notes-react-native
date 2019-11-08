# REDUCER

Function to manage changes to object.

When multiple pieces of data are closely related (e.g., RGB values of color), and there is set of precise ways to manipulate data, can be managed by **reducer**.

Takes 2 args: object of all state, object describing update. Use arg #2 to determine how to change arg #1. However, never change arg #1 directly. Always return new state.

State is managed by either hook `useReducer` or `useState`, never both.

```javascript
// setup
import React, { useReducer } from 'react';
...
const [state, dispatch] = useReducer(reducer, { red: 0, green: 0, blue: 0 });
  const { red, green, blue } = state;

// call reducer
dispatch({ type: 'change_red', payload: COLOR_DELTA });

// define reducer
const reducer = (state, action) => {
  // state === { red: number, green: number, blue: number }
  // action === { type: 'change_red' || 'change_green' || 'change_blue', payload: number }

  switch (action.type) {
    case 'change_red':
      let newRed = state.red + action.payload;
      newRed = newRed > 255 ? 255: (newRed < 0 ? 0 : newRed);
      return { ...state, red: newRed };
    case 'change_green':
        let newGreen = state.green + action.payload;
        newGreen = newGreen > 255 ? 255: (newGreen < 0 ? 0 : newGreen);
      return { ...state, green: newGreen };
    case 'change_blue':
        let newBlue = state.blue + action.payload;
        newBlue = newBlue > 255 ? 255: (newBlue < 0 ? 0 : newBlue);
      return { ...state, blue: newBlue };
    default:
      return state;
  }
};
```

## Action Object Convention

```javascript
{ type: 'change_red', payload: 15 }
```

`type`: String describing change operation.

`payload`: Data critical to operation.
