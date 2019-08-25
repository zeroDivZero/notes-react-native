# STYLES

In JS syntax, not CSS. Can create styles object in same component file or separate.

Use `StyleSheet.create()` to add validation (error if style format incorrect).

```javascript
import { StyleSheet } from 'react-native';

const styles = StyleSheet.create({
    textStyle: {
        fontSize: 30
    }
})
```

Can also use plain style object, but only get warning.

```javascript
const styles = {
    textStyle: {
        fontSize: 30
    }
}
```

## Format

Most properties similar to CSS, but camel case instead of hyphened text.

```font-size``` -> ```fontSize```

## Apply

```javascript
const Header = () => {
    const { textStyle } = styles;
    return <Text style={textStyle}>Welcome!</Text>;
}
```

Inline:

```jsx
<Text style={{fontSize: 30}}>Welcome!</Text>
```

Multiple:

```jsx
<Text style={[textStyle, {fontWeight: 'bold'}]}>Welcome!</Text>
```
