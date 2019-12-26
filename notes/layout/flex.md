# FLEX

Laying out children.

## `flexDirection`

Direction children are laid out.

* `column` (default): Children laid out vertically, top to bottom.
* `row`: Children laid out horizontally, left to right.

## `alignItems`

Layout of children in direction perpendicular to `flexDirection`.

* `stretch` (default): Children expand to fully fill axis.
* `flex-start`: Minimize children space, align left/top.
* `center`: Minimize children space, align center.
* `flex-end`: Minimize children space, align right/bottom.

```javascript
const styles = StyleSheet.create({
  viewStyle: {
    borderWidth: 3,
    borderColor: "black",
    alignItems: "flex-end"
  }
};
```

## `justifyContent`

Layout of children along **primary axis** (dir specified in `flexDirection`). Opposite of `alignItems`.

* `flex-start` (default): Justify top/left.
* `center`: Justify center.
* `flex-end`: Justify bottom/right.
* `space-between`: Equal space between each pair. No space at edges.
* `space-around`: Equal space between each pair. Some space at edges.

## `flex`

Determines how much space child takes up. Specify numeric value. Actual space relative to ratio of this child's value to total of values specified.

If specified `1` and other children do not specify, takes up as much space as possible while minimizing other children.

Applies to primary axis.

```css
textOneStyle: {
  borderWidth: 3,
  borderColor: 'red',
  flex: 4
},
textTwoStyle: {
  borderWidth: 3,
  borderColor: 'red',
  flex: 4
},
textThreeStyle: {
  borderWidth: 3,
  borderColor: 'red',
  flex: 2
}
```

## `alignSelf`

Applies to child, overrides parent's `alignItems`. Has same values as `alignItems`.
