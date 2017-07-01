# Communicating with a Server

In this exercise, you will enable an app to talk to a server using `redux-thunk`. We will call the [Reddit API](https://www.reddit.com/r/TheoryOfReddit/wiki/collecting_data).

1. Clone the repo [reddit-app](https://github.com/petermunro/reddit-app). Now `npm install`, then `npm start`.

1. Add in the Redux devtools store enhancer so you can use the devtools extension.


###### Fetch Data

1. In `src/actions/index.js`, the `fetchPosts()` function needs to be defined.

    1. First, dispatch a `requestPosts()` action, passing it the required 'reddit' (eg 'reactjs' or 'frontend').

    2. Now return a promise from this function, as a result of calling `fetch`:

            return fetch(URL)
            .then( )    // convert from JSON
            .then( )    // dispatch an action for the received posts (see below)

        - For the URL, <https://www.reddit.com/r/reactjs> would take you to the 'reactjs' reddit. If you append `.json`, it will retrieve this same page as JSON.

    3. When the data arrives, dispatch a further action using the `receivePosts()` action creator.

4. Test your work using the browser devtools (`Network` tab, `Redux` tab and `React` tab).

   Which actions are dispatched, and how do they change the state tree?


###### Enable the Refresh button

The `Refresh` button doesn't yet work. To enable it, in `containers/App.js` dispatch two further actions:

1. The first should invalidate the selected reddit by dispatching the `invalidateReddit()` action. What parameters does this require? How does this update the state tree?

1. The second should fetch new posts if required. Dispatch `fetchPostsIfNeeded()`, again passing in the required parameter(s).


###### Stretch Goals

1. If the app goes offline (devtools `Network` ➞ `Offline`), the `fetch` doesn't succeed. Add a way to propagate the error to the UI.

1. Enhance the app to enable you to click on a post to retrieve the corresponding comments.


