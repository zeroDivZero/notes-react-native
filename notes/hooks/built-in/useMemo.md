# `useMemo`

```js
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

Returns memoized value.

Pass "create" function and array of dependencies. `useMemo` only recomputes memoized value when one of dependencies has changed. Avoids expensive calculations on every render.

Function passed to `useMemo` runs during rendering. If no array provided, new value computed on every render.
