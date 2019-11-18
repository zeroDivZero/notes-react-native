# TEXTINPUT

For inputting text via keyboard. Use props to configure features like auto-correction, auto-capitalization, placeholder text, and different keyboard types (e.g., numeric keypad).

By default has minimal style besides height. Not visible against white background.

Subscribe to event `onChangeText` to read user input. There are also other events like `onSubmitEditing` and `onFocus`. Minimal ex:

```javascript
import React, { Component } from 'react';
import { TextInput } from 'react-native';

export default function UselessTextInput() {
  const [value, onChangeText] = React.useState('Useless Placeholder');

  return (
    <TextInput
      style={{ height: 40, borderColor: 'gray', borderWidth: 1 }}
      onChangeText={text => onChangeText(text)}
      value={value}
    />
  );
}
```
