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

## How It Works

Passed to RN Bundler, which uses **Babel** to turn into JS code.

In:

```javascript
const profile = (
  <div>
    <img src="avatar.png" className="profile" />
    <h3>{[user.firstName, user.lastName].join(' ')}</h3>
  </div>
);
```

Out:

```javascript
const profile = React.createElement("div", null,
  React.createElement("img", { src: "avatar.png", className: "profile" }),
  React.createElement("h3", null, [user.firstName, user.lastName].join(" "))
);
```

## Variable

Can insert value of variable with `{}`. Can assign entire JSX to variable.

```jsx
const OneComponent = () => {
  const firstName = 'John';
  const email = <Text>abc@somecompany.com</Text>;

  return (
  <View>
    <Text>Hi there, {firstName}.</Text>
    <Text>Please contact:</Text>
    {email}
  </View>
  );
};
```
