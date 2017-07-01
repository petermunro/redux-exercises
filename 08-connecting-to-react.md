# Connecting to React



The next step is to connect to React using `react-redux`. Use the document [here](http://redux.js.org/docs/basics/UsageWithReact.html) to help you.

1. Install `react-redux`:

        npm install --save react-redux

1. Create container components using `connect()` together with `mapStateToProps()` and `mapDispatchToProps()`.

1. Pass the store down by wrapping the top-level `App` component in a `Provider`.

> Oh! I forgot to say: for point (3) you'll need to wrap your `App` component in a `Provider`, passing in the store, like this:

```
render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
)
```

> See [here](http://redux.js.org/docs/basics/UsageWithReact.html#passing-the-store) for details.

