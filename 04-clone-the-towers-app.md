# Clone the Towers App

Clone the _towers_ app from [here](https://github.com/petermunro/towers-app), run `npm install`, then `npm start`.

The _towers_ app displays a tower with two buttons: _Raise_ and _Lower_, which raise and lower the tower respectively.

Its purpose is as a teaching aid in learning Redux. :-)

1. This app doesn't (yet) use `react-redux`. How is the view updated?

## Add Redux to this app

We will now add Redux to this app.

### Install

Install redux and react-redux:

`npm install redux react-redux --save`

### Create the store

Create the store. To do this, create a new file, `store.js`.

1. Import `createStore` from redux.
2. Import `towersReducer` from your reducers file (which you will create in the next step).
3. Initialize the store by calling `createStore` and passing it your reducer.

### Create the reducer

Create the reducer. To do this, create the reducers file (which you
imported in the previous step).

1. Export the reducer function. It should take as arguments the `state` object (which it should default to a default state) and
   an `action`.
2. Your reducer file will check the state and action and return a
   new state, so it needs to know the action types! Import two constants
   from an actions file (which again you will create in a moment). For example:

   ```javascript
   import { RAISE_ACTION, LOWER_ACTION } from "./actions/towers";
   ```

3. Create a `switch` statement on the `action.type` (one of the action constants you imported in the previous substep), for example:

   ```javascript
    switch(action.type) {
        case ADD_ACTION:
            return {
               ...
   ```

4. In the body of each `case`, return an object representing the new state, based on the action type and the current state. Remember to use immutable programming!

5. The `default` case should just return the current state.

### Create the action constants and action creators

1. Action constants are just constants for the actions. You imported
   these in the previous step. The value is a string, eg 'RAISE'.

2. Write the action creators. These functions (eg `createRaiseAction()`)
   should return an action object, for example:

   ```javascript
   {
      type: RAISE_ACTION,
   }
   ```

### Wire up the UI - Wrap with a Provider

We will now replace local component state with Redux.

First step is to edit `index.js` and wrap our component tree in a `<Provider>`:

1. In `index.js`, import the (named import) `Provider` from redux.

2. Import your store from the file you created it in.

3. Wrap the entire app in the Provider, for example:

   ```javascript
   ReactDOM.render(
     <Provider store={towersStore}>
       <React.StrictMode>
         <App />
       </React.StrictMode>{" "}
     </Provider>,
     document.getElementById("root")
   );
   ```

### Wire up the UI - Get your App talking to Redux!

Now to wire the App to Redux. We will again use `react-redux`
with its hooks.

1. Import the (named) `useDispatch` and `useSelector` from react-redux.

2. Import your action creator functions.

3. Remove any local state corresponding to the height of the tower.

4. In the `App` component, create a `dispatch` variable from `useDispatch()`.

5. Again in the `App` component, create a `height` variable from a call to
   `useSelector()`. This takes as an argument a function that retrieve the part of the state object that you want. For example:

   ```javascript
   useSelector((state) => state.height);
   ```

   Assign this to your height variable.

6. In the `raise()` and `lower()` functions, remove any code that uses local state. Replace it with a call to `dispatch()`. This should take as argument a call to the appropriate action creator you imported earlier.

Run the app and see if it works!
