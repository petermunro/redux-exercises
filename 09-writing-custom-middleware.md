# Writing Custom Middleware

#### A Timing Middleware

Write and test a 'timing' middleware function that measures how long an action takes to run.

To perform the timing measurements, you can use either:

1. the browser console methods `console.time()` and `console.timeEnd()` (https://developer.mozilla.org/en-US/docs/Web/API/Console/time); or
2. the browser High Resolution Time API (https://developer.mozilla.org/en-US/docs/Web/API/Performance/now)

######  Applying our Middleware

You might have noticed that the `createStore()` function only allows us to provide a single store enhancer or middleware. Here's the signature:

    function createStore(reducer, preloadedState, enhancer) { ... }

And we've used up our one slot for our devtools!

```
const store = createStore(
  myReducer,
  window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__()
);
```

So, to have _both_ our Redux devtools _and_ our middleware, we do this:

```
import { createStore, applyMiddleware, compose } from 'redux';

// ...

let myMiddlewares = [
  timingMiddleware,
];

const composeEnhancers = window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__ || compose;
const enhancer = composeEnhancers(
  applyMiddleware(...myMiddlewares),
);
const store = createStore(myReducer, enhancer);
```

- Middleware is a form of enhancer, but with a different function signature, so we apply it by calling the function `applyMiddleware()`
- The `composeEnhancers` line checks that we have the Redux devtools browser extension installed

For more details, see the [Redux devtools documentation on creating your store](https://github.com/zalmoxisus/redux-devtools-extension#12-advanced-store-setup).

---
[Possible [solution](https://gist.github.com/petermunro/95a8a2bf6bd466d22899529de32438b6)]

