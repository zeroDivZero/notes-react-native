# `compose`

To bundle multiple functions into one (not directly applicable to state).

E.g., instead of:

```js
const double = (num) => num * 2;
const square = (num) => num * num;
const half = (num) => num / 2;

const halfSquareDouble = (num) => half(square(double(num)));

console.log(halfSquareDouble(2)); // 8
```

do:

```js
import { compose } from "redux";

const halfSquareDouble = compose(half, square, double);

console.log(halfSquareDouble(2)); // 8
```
