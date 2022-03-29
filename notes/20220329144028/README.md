# Show error message in action properly

## Issue

Setting an action allows you to set a "Precondition" when the action
will be available. For example you want to set the action `Finish` only
when the record status is `ready` and not `draw`.

Doing it this way the user will not see the action until the status of
the record is `ready`.

But if you want the action be available for the user and show an error
message it could be cumbersome without a proper configuration:

- Send a `sys.ui.sendMessage()` and return in your code will also send a
  success message to the UI. Because the action it executed well.
- Throw an exception will do the trick, but also send a notification to
  the developer.

## Solution

We may want to keep using the `sys.ui.sendMessage()` method. But this
time updating the view settings of the action itself and turn off the
`Show success message` flag.

This will avoid that weird success message after we return the error
message.

- `Action > Views > actionName` - Show success message

## Additional note

We probably want to code a success message if the action run properly as
we disabled the default success message.

```js
if (error) {
  return sys.ui.sendMessage({
    scope: 'global',
    name: 'actionFailed',
    title: 'Action Failed',
    message: 'Something went wrong!',
    type: 'error',
    keepVisible: true
  });
}

// Action stuff here...

return sys.ui.sendMessage({
  scope: 'global',
  name: 'actionSuccess',
  title: 'Success',
  message: 'Action was executed correctly',
  type: 'success',
});
```
