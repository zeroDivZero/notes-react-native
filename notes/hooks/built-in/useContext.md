# `useContext`

```js
const value = useContext(MyContext);
```

Accepts context object (from `React.createContext`) and returns current value. Current context value determined by `value` prop of nearest `<MyContext.Provider>` above calling component in tree.

When nearest `<MyContext.Provider>` above component updates, this hook triggers rerender with latest context value passed to that provider. Even if ancestor uses `React.memo` or `shouldComponentUpdate`, rerender still happens starting at component itself using `useContext`.
