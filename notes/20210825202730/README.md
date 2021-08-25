# Action's fields

When trigger an action you can set parameters and ask for more
information to handle it.

Then use `action.field('fieldName')`.

```js
function (record, oldRecord, action) {
  if (action.field('isThisChecked').val()) {
    // Do something
  } else {
    // Do other thing
  }
}
```
