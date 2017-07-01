# Pure Redux: Adding a Store Enhancer

Earlier you looked at a pure Redux-only app.

The Redux store can be 'enhanced' with a _store enhancer_.

1. Add this function to the app's `index.js`:


        function myEnhancer(createStore) {
          console.log('myEnhancer');

          return function(reducer, preloadedState) {
            console.log('Enhancing store...');

           let realStore = createStore(reducer, preloadedState);
            let enhancedStore = {
              dispatch(action, reducer) {
                console.log('enhancedStore: dispatch', action);
                return realStore.dispatch(action, reducer);
              },
              getState() {
                console.log('enhancedStore: getState');
                return realStore.getState();
              },
              subscribe(listener) {
                console.log('enhancedStore: subscribe');
                return realStore.subscribe(listener);
              }
            };
            return enhancedStore;
          }
        }

1. What data type does the enhancer return? Which fields does it contain?

1. Modify the `createStore()` call from this:

        let store = createStore(contactReducer);

  to this:

        let store = createStore(contactReducer, myEnhancer);

1. Run the app again (`npm start`) to ensure the enhancer runs. What does it do?

