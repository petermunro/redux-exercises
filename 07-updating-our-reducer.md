
# Updating our Reducer

The client is being a little picky! They'd now like to have:

- multiple "columns", each of which can be set to its own height
- the ability to add and remove columns
- a panel that displays the total number of columns, as well as a name provided by the user to name this configuration of columns

So:

1. How does our state need to change to reflect this new set of requirements?
1. What action types will be needed?
1. What might the action creator functions look like?
1. Given these actions, how does the state need to change for each one?

It looks like it's time to refactor our app a little and add in these action creators.

Also, update the reducer and implement the functionality needed.

Examine your new state object in the Redux devtools.

