# Using the Redux Devtools

In this exercise you'll install and use the Redux Devtools.

1. Install the [Redux devtools](http://extension.remotedev.io) extension in your browser.

2. The extension needs to talk to Redux to be able to display and manipulate the store and actions, and so on, so you'll need to modify your app's code as described [here](http://extension.remotedev.io/#1-with-redux).

3. Once you have it installed, open your browser developer tools and navigate to the `Redux` tab.

4. Use your app's UI so that it dispatches some actions. Ensure that you can:

  - see these when these actions are dispatched, they appear in the log
  - inspect each action by clicking the `Action` tab in the right-hand pane
  - view the app's state (`State` tab) corresponding to the selected action

### Notes on Using Redux Devtools
Dan Abramov first demonstrated Redux with _time travel debugging_. His vision of developing using the Redux devtools is described [here](https://medium.com/@zalmoxis/improve-your-development-workflow-with-redux-devtools-extension-f0379227ff83).

