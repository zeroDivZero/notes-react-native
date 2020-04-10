# PROPS

[RN A11y Doc](https://reactnative.dev/docs/accessibility)

## `accessible` (iOS, Android)

`true` means view is a11y element and groups its children into single selectable component. By default, all touchable elements are accessible.

On Android, `accessible={true}` translates to native `focusable={true}`.

```jsx
<View accessible={true}>
  <Text>text one</Text>
  <Text>text two</Text>
</View>
// no a11y focus on 'text one' and 'text two'
```

## `accessibilityLabel` (iOS, Android)

VoiceOver reads this string when user selects associated element. Should be set when element accessible.

```jsx
<TouchableOpacity
  accessible={true}
  accessibilityLabel="Tap me!"
  onPress={this._onPress}>
  <View style={styles.button}>
    <Text style={styles.buttonText}>Press me!</Text>
  </View>
</TouchableOpacity>
// accessibilityLabel on TouchableOpacity would default to "Press me!" - concatenating all Text node children separated by spaces
```

## `accessibilityHint` (iOS, Android)

Helps user understand what will happen when they perform action on element. Set if behavior not apparent from a11y label.

```jsx
<TouchableOpacity
  accessible={true}
  accessibilityLabel="Go back"
  accessibilityHint="Navigates to the previous screen"
  onPress={this._onPress}>
  <View style={styles.button}>
    <Text style={styles.buttonText}>Back</Text>
  </View>
</TouchableOpacity>
```

As of writing, iOS VoiceOver can set to skip hints, but not Android TalkBack.

## `accessibilityIgnoresInvertColors` (iOS)

iOS allows inverting screen colors to make easy reading for people with brightness sensitivity, color blindness, or low vision. Set this to `true` if views like photos shouldn't be inverted.

## `accessibilityRole` (iOS, Android)

Communicates purpose of component. Example roles below; see official doc for complete list.

`none`: Element has no role.

`button`: Element should be treated as button.

`link`: Element should be treated as link.

`search`: Text field element should also be treated as search field.

`image`: Element should be treated as image. Can be combined with `button` or `link`, for example.

`text`: Used when element should be treated as static text.

`adjustable`: Element can be "adjusted" (e.g., slider).

## `accessibilityState` (iOS, Android)

Object describing state of component. Can contain following fields, all optional:

`disabled`: Boolean, if element is disabled.

`selected`: Boolean, if selectable element is currently selected.

`checked`: Boolean or `"mixed"`, indicates state of checkable element.

`busy`: Boolean, if element is currently busy.

`expanded`: Boolean, if expandable element is expanded.

## `accessibilityValue` (iOS, Android)

Object representing component value. Can be text, or, for range-based components like sliders and progress bars, range info (minimum, current, and maximum). Can contain following fields:

`min`: Int, min value of range. Required if `now` is set.

`max`: Int, max value of range. Required if `now` is set.

`now`: Int, current value of range.

`text`: Textual description of value. Overrides `min`, `now`, and `max` if set.

## `accessibilityViewIsModal` (iOS)

If VoiceOver ignores elements within sibling views of receiver.

For example, views A and B are siblings. Set `accessibilityViewIsModal` to `true` on view B causes VoiceOver to ignore elements in view A. If view B contains child view C with `accessibilityViewIsModal` set, VoiceOver does not ignore elements in view A.

## `accessibilityElementsHidden` (iOS)

If a11y elements contained within this a11y element are hidden.

For example, setting `accessibilityElementsHidden` to `true` on a view causes VoiceOver to ignore elements in that view. Similar to Android property `importantForAccessibility="no-hide-descendants"`.

## `onAccessibilityTap` (iOS, Android)

Assign function to be called when someone activates accessible element by double tapping on it while it's selected.

## `onMagicTap` (iOS)

Assign function to be called when performing "magic tap" gesture, which is double-tap with two fingers.

For example, in iPhone Phone app, magic tap answers phone call or ends current one. If selected element does not have `onMagicTap`, system traverses up view hierarchy until it finds view that does.

## `onAccessibilityEscape` (iOS)

Assign function to be called when performing "escape" gesture, which is two finger Z shaped gesture. Should move back hierarchically (up or back in navigation hierarchy, or dismiss modal).

If selected element does not have `onAccessibilityEscape`, system traverses up view hierarchy until it finds view that does, or bonks to indicate it was unable to find one.

## `accessibilityLiveRegion` (Android)

Lets TalkBack alert user when components dynamically change. Can be of following values:

`none` A11y services should not announce changes to this view.

`polite` A11y services should announce changes to this view.

`assertive` A11y services should interrupt ongoing speech to immediately announce changes to this view.

```jsx
<TouchableWithoutFeedback onPress={this._addOne}>
  <View style={styles.embedded}>
    <Text>Click me</Text>
  </View>
</TouchableWithoutFeedback>
<Text accessibilityLiveRegion="polite">
  Clicked {this.state.count} times
</Text>
```

In above example method `_addOne` changes `state.count`. When user taps `TouchableWithoutFeedback`, TalkBack reads text in `Text` because of its `accessibilityLiveRegion="polite"` property.

## `importantForAccessibility` (Android)

In case of 2 overlapping UI components with same parent, default a11y focus can have unpredictable behavior. Set this so view fires a11y events and is reported to a11y services. It can be `auto`, `yes`, `no`, and `no-hide-descendants` (last value forces a11y services to ignore component and children).

```jsx
<View style={styles.container}>
  <View style={{position: 'absolute', left: 10, top: 10, right: 10, height: 100,
    backgroundColor: 'green'}} importantForAccessibility="yes">
    <Text> First layout </Text>
  </View>
  <View style={{position: 'absolute', left: 10, top: 10, right: 10, height: 100,
    backgroundColor: 'yellow'}} importantForAccessibility="no-hide-descendants">
    <Text> Second layout </Text>
  </View>
</View>
```

In above example, yellow layout and descendants are invisible to TalkBack and other a11y services.
