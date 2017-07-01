# Middleware for Dispatching Functions

#### Dispatching _Functions_?

1. Add this middleware to your app. It enables you to dispatch functions:

        const dispatchAFunction = store => next => action => {
          if (typeof action === 'function') {
            action(store.dispatch, store.getState);
          } else {
            next(action);
          }
        }

  As you can see, it's quite simple. If you dispatch a function to it, it will call it, providing it with two parameters:

  - `dispatch` (so in your function you can dispatch further actions); and
  - the store's `getState()` function too, so you can retrieve state.

  <br />

1. Now call this from within your app. For example, when you click 'Higher', you could force an extra 'INCREASE'.

  To do this, in your _towers_ `App`'s `handleAdd()` callback, you could do:

        handleAdd = () => {
          console.log(`add`);
          this.props.higher();
          this.props.higherAgain((dispatch, getState) => {
            dispatch(higher());
          } );
        }

1. __Refactoring to Action Creators__ Let's refactor to Action Creators if you haven't already done so. Change `handleAdd()`:

        handleAdd = () => {
          console.log(`add`);
          this.props.store.dispatch(higher());
          this.props.store.dispatch(higherAgain());
        }

  And the Action Creators could look like this:

        function higher() {
          return { type: INCREASE };
        }

        function lower() {
          return { type: DECREASE };
        }

        function higherAgain() {
          return function(dispatch, getState) {
            dispatch(higher());
          }
        }

1. Now change `higherAgain()` so that it does a `DECREASE`.  (OK, maybe you'd better change it to call `lower()`. 😀) The column should stay the same height when you hit 'Higher'.

1. Modify this `DECREASE` dispatch so that the tower is decreased one second after pressing the button.

  You have now dispatched an _asynchronous action_. Instead of updating the state immediately (synchronously), it updated it some time later (asynchronously).


#### Logger

A `redux-logger` middleware is available [here](https://github.com/evgenyrodionov/redux-logger), which you can install and apply it to your app.

