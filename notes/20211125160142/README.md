# Use `sys.users.containsGroup()` to check if user belongs to a group

You can check if a user has a group or not.

```js
var user = sys.context.getCurrentUserRecord();
if (sys.users.containsGroup(user, 'admins')) {
  // Do admin stuff 😎
} else {
  sys.logs.error('You are not allowed to do this');
}
```
