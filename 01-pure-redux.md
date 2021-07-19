# A Simple Pure Redux App

In this exercise you will look at Redux only, without any React or even a UI (apart from a terminal console). The app is a simple command line demo.

1. Clone this repo, `npm install` and `npm start` it: <https://github.com/petermunro/redux-only>

1. Follow the output of the app after the line:

   `-------- START OF APP --------`

   Relate the output statements to the source code in `src/index.js`.

1. Look through the source
   file `src/index.js`, and answer:

   1. What does the **state object** look like?
   1. How is the **store** created?
   1. How is the app informed about updates to the store?
   1. When informed, how does the app retrieve the store's state?
   1. How are actions dispatched?
   1. What _is_ an action?
   1. What happens to the action defined, once dispatched?
   1. How is the store changed after the action has been dispatched?

1. Try dispatching a further action, containing your own data, and view the store's state to verify it has been updated as you expect.
