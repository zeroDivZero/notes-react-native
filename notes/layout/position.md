# POSITION

## `position`

Positions child to absolute position, overriding box obj model and flex box.

* `relative` (default): No override.
* `absolute`: Ignored by siblings. Still obeys some flex box rules set by parent (but not `alignItems: 'stretch'`).

## `top`, `bottom`, `left`, `right`

Similar to margins, but applied to child _after_ children are laid out.

Ex: Move down 10px (add 10px margin to top), but siblings not affected (overlap may occur).

```css
textStyle: {
  borderWidth: 3,
  borderColor: 'red',
  fontSize: 18,
  top: 10
}
```

If `position: absolute` and `0` specified for all 4 edges, child fills parent completely:

```css
textStyle: {
  borderWidth: 3,
  borderColor: 'red',
  fontSize: 18,
  position: 'absolute',
  top: 0,
  bottom: 0,
  left: 0,
  right: 0
},
```

Or simply:

```css
textStyle: {
  borderWidth: 3,
  borderColor: 'red',
  fontSize: 18,
  ...StyleSheet.absoluteFillObject
},
```
