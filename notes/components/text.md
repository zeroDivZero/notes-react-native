# TEXT

For displaying text. Supports nesting, styling, and touch handling.

```jsx
<Text style={{fontFamily: 'Cochin'}}>
  <Text style={[{fontSize: 30}, {fontWeight: 'bold'}]} onPress={this.onPressTitle}>
    Welcome{'\n'}{'\n'}
  </Text>
  <Text numberOfLines={5}>
    What is your name?
  </Text>
</Text>
```
