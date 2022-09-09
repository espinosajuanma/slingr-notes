# Re-direct to another view with `sys.ui` message

This is a trick I never use but Pablo show me he did to use the
`sys.ui.sendMessage` method to re-direct the user after a record being
created.

He used to solve a problem: the user didn't have permissions to the
record he just created. So to avoid the error message "You have not
permissions to see this record" he redirect the user back to the grid
view.

Anyway I think it can be helpful in other ways so this is the snippet:

```js
sys.ui.sendMessage({
  scope: 'global',
  name: 'navigate',
  view: 'generalFeedback'
});
```
