# Use `getCurrentUserRecord()` in permission script

If you have a setting entity and want to check if the current user is
the same, you shouldn't use the `record` parameter of the function. This
record is an instance of the entity you are changing the permission.

Instead use `sys.context.getCurrentUserRecord()` to compare.


```js
function (record, parentField, action) {
  var user = sys.context.getCurrentUserRecord();
  return app.settings.getPayrollAccountant().id() === user.id();
}
```
