# ANDROID

## Send Event

To trigger a11y event on UI component (e.g., when custom view appears on screen or set a11y focus to view), native `UIManager` module exposes `sendAccessibilityEvent`. Takes 2 args: view tag and event type. Supported types are `typeWindowStateChanged`, `typeViewFocused`, and `typeViewClicked`.

```javascript
import { Platform, UIManager, findNodeHandle } from 'react-native';

if (Platform.OS === 'android') {
  UIManager.sendAccessibilityEvent(
    findNodeHandle(this),
    UIManager.AccessibilityEventTypes.typeViewFocused);
}
```
