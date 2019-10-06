# STACK NAVIGATOR

By default familiar stack navigation look & feel: new screen slides from right on iOS, bottom on Android. Can be modal from bottom on iOS.

```javascript
import { createStackNavigator, createAppContainer } from 'react-navigation';
import { Screen1 } from './src/screen/screen1';
import { Screen2 } from './src/screen/screen2';
import { Screen3 } from './src/screen/screen3';

const navigator = createStackNavigator(
  {
    Home: Screen1,
    Blog: Screen2,
    About: Screen3
  },
  {
    initialRouteName: 'Home',
    defaultNavigationOptions: {
      title: 'App'
    }
  }
);

export default createAppContainer(navigator);
```

To navigate, use `navigation.navigate()` that's passed to component as part of `props`, and specify route:

```javascript
const Screen1 = ({ navigation }) => {
  return (
    <View>
      <Button
        onPress={() => navigation.navigate('Blog')}
        title="Go to Blog"
      />
      <Button
        onPress={() => navigation.navigate('About')}
        title="Go to About"
      />
    </View>
  );
};
```
