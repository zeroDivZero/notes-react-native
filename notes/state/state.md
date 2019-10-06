# STATE

Track data that change over time. If changes, rerender.

For each piece of data, answer 3 questions:

1. What is it?
2. What type is it?
3. What is its default value?

To add to state, use **hook** `useState` and provide default value:

```javascript
import React, { useState } from 'react';

const [counter, setCounter] = useState(0);

<Button title="Increase" onPress={() => { setCounter(counter + 1); }} />
```

Should not modify state directly. When `setCounter` used, rerender component.
