# Pure Redux: Adding a Store Enhancer

Earlier you looked at a pure Redux-only app.

The Redux store can be 'enhanced' with a _store enhancer_.
This lets you add functionality to the store, but here we're
creating a simple enhancer to show the concept and to lay the
groundwork for later.

1.  Here's our store enhancer. As you can see, it doesn't enhance the store by much! It just adds a few `console.log`s.

    Add this function to the app's `index.js`:

    ```javascript
    function myEnhancer(createStore) {
      console.log("myEnhancer");

      return function (reducer, preloadedState) {
        console.log("Enhancing store...");

        let realStore = createStore(reducer, preloadedState);
        let enhancedStore = {
          dispatch(action, reducer) {
            console.log("enhancedStore: dispatch", action);
            return realStore.dispatch(action, reducer);
          },
          getState() {
            console.log("enhancedStore: getState");
            return realStore.getState();
          },
          subscribe(listener) {
            console.log("enhancedStore: subscribe");
            return realStore.subscribe(listener);
          },
        };
        return enhancedStore;
      };
    }
    ```

1.  What JavaScript data type does the enhancer return?

1.  What are the names of the fields it contains?

1.  Let's add the store enhancer to our store.
    Modify the `createStore()` call from this:

         let store = createStore(contactReducer);

to this:

        let store = createStore(contactReducer, myEnhancer);

1. Run the app again (`npm start`) to ensure the enhancer runs. Identify when the various `console.log`s get called.
