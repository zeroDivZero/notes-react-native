# ACTIONS

Allow assistive tech to programmatically invoke actions of component. To support actions, component must:

1. Define supported actions via `accessibilityActions` prop.
2. Implement `onAccessibilityAction` to handle action requests.

`accessibilityActions` should contain list of action objects, each with fields:

1. `name` (string, required)
2. `label` (string, optional)

Action can be standard like tapping button or adjusting slider, or custom like deleting email.

## Standard

`name` must be:

* `magicTap` - iOS only - While VoiceOver focus on or inside component, user double tapped with 2 fingers.
* `escape` - iOS only - While VoiceOver focus on or inside component, user performed two finger scrub gesture (left, right, left).
* `activate` - Activate component. Typically same action as when user touches or clicks component normally. Generated when screen reader user double taps component.
* `increment` - Increment adjustable component. On iOS, VoiceOver generates this action when component has role `adjustable` and user places focus on it and swipes upward. On Android, TalkBack generates this action when user places a11y focus on component and presses volume up button.
* `decrement` - Decrement adjustable component. On iOS, VoiceOver generates this action when component has role `adjustable` and user places focus on it and swipes downward. On Android, TalkBack generates this action when user places a11y focus on component and presses volume down button.
* `longpress` - Android only - Generated when user places a11y focus on component and double-tap-and-holds one finger on screen. Typically, this should perform same action as when user holds down one finger on component normally.

## Custom

`label` is localized string containing action description. Optional for standard, and often unused by assistive tech.

## Request

Component must implement `onAccessibilityAction`. Arg is event containing action name.

```jsx
<View
  accessible={true}
  accessibilityActions={[
    {name: 'cut', label: 'cut'},
    {name: 'copy', label: 'copy'},
    {name: 'paste', label: 'paste'},
  ]}
  onAccessibilityAction={(event) => {
    switch (event.nativeEvent.actionName) {
      case 'cut':
        Alert.alert('Alert', 'cut action success');
        break;
      case 'copy':
        Alert.alert('Alert', 'copy action success');
        break;
      case 'paste':
        Alert.alert('Alert', 'paste action success');
        break;
    }
  }}
/>
```
