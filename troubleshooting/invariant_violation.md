# INVARIANT VIOLATION

## Text strings must be rendered within a `<Text>` component.

Cannot render text not wrapped in `<Text>`. Often this is due to using `&&` instead of `?:` for conditional rendering. When condition is `undefined`, `&&` doesn't return component.

Instead of:

```jsx
widgetNumber === 10 && <MyComponent />
```

do:

```jsx
widgetNumber === 10 ? <MyComponent /> : null
```

## Element type is invalid

Component not imported properly. Exported as default but importing as named, or vice versa.
