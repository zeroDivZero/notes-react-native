# HELLO WORLD

```jsx
import React from 'react';
import { Text, View } from 'react-native';

const HelloWorldApp = () => {
  return (
    <View
      style={{
        flex: 1,
        justifyContent: "center",
        alignItems: "center"
      }}>
      <Text>Hello, world!</Text>
    </View>
  );
};

export default HelloWorldApp;
```

## Component Anatomy

1. Import libs.

   ```jsx
   import React from 'react';
   import { Text, StyleSheet } from 'react-native';
   ```

   `react` lib manages how components work together. `react-native` renders components to device screen.

2. Create function component. Returns in `JSX` syntax.

   ```jsx
   const MyComponent = () -> {
     return <Text style={styles.text}>Hello world!</Text>;
   };
   ```

   To return multiline, use `()`, or opening tag must be on same line as `return`:

   ```jsx
   return (
   <View>
     <Text>some text</Text>
   </View>
   );
   ```

   ```jsx
   return <View>
     <Text>some text</Text>
   </View>;
   ```

3. Style component.

   ```jsx
   const styles = StyleSheet.create({
     text: {
       fontSize: 30
     }
   });
   ```

4. Export component.

   ```jsx
   export default MyComponent;
   ```

## `App.js`

To test component quickly, edit `App.js`:

```js
import MyComponent from "./src/components/MyComponent";
```

Modify `navigator` to include `MyComponent` and set it as `initialRouteName`.

```js
const navigator = createStackNavigator(
  {
    Home: HomeScreen,
    MyComponent: MyComponent
  },
  {
    initialRouteName: "MyComponent",
    defaultNavigationOptions: {
      title: "App"
    }
  }
);
```

Uses `react-navigation` lib to manage screen navigation.
