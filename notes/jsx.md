# JSX

JS syntax extension (to embed XML within JS). Sugar of JS funcs. Can be used in React, but highly recommended for RN to describe UI appearance.

```jsx
<View><Text>Hello world!</Text></View>
```

```jsx
const element = <h1>Hello, world!</h1>;
```

Many frameworks embed code inside markup; reversed in React: JSX allows markup inside code. Looks like HTML, but uses components. Ex: `<Text>` is built-in component that displays text, and `<View>` is like `<div>` or `<span>`.

Web dev often separates techs: markup (HTML), styling (CSS), and control logic (JS). JSX prioritizes separation of concerns. Markup, styles, and behavior can live in single file for each component. **.js** files in RN are in fact JSX files.
