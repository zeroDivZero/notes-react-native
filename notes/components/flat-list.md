# FLATLIST

Performant interface for rendering flat list. Supports many features like header, footer, separator, pull-to-refresh, multi-column, horizontal mode, etc.

If need sections, use `<SectionList>`.

## Usage

Requires `data` and `renderItem` props.

```jsx
<FlatList
  data={[{key: 'a'}, {key: 'b'}]}
  renderItem={({item}) => <Text>{item.key}</Text>}
/>
```

`renderItem` specifies func that takes 1 param (a data element) and returns how it's rendered.

```jsx
renderItem={(element) => {
  // element === { item: {key: 'a'}, index: 0 }
}}
```

Note `element` not simply element of data array; it contains extra `index` property. If index not needed, can use destructuring to get data element directly:

```jsx
renderItem={({ item }) => {
  // item === { key: 'a' }
}}
```

## Item Key

If data element doesn't have prop `key` (get warning), every time an element is inserted/removed, RN removes entire list from screen and re-creates it. `key` binds data to element on screen, so RN can update more efficiently.

`key` must be unique string.

### keyExtractor

If don't want to add `key` to data, can provide func to have `FlatList` extract key automatically:

```jsx
<FlatList
  keyExtractor={item => item.uniqueId}
  ...
/>
```

## Horizontal

Make list horizontally scrolling by specifying `horizontal` prop. Equivalent to `horizontal={true}`.

```jsx
<FlatList>
  horizontal
  ...
/>
```

Hide horizontal scroll bar with `showsHorizontalScrollIndicator={false}`. Similarly, there's a vertical counterpart.

## Item Size

Use styling to set dimensions, margins, etc. for item.
