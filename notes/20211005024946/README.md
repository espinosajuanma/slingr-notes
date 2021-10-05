# Don't pass `action` as a parameter to a library function

Keep it in separated parameters.

**Don't:**

```js
function (record, oldRecord, action) {
  app.myLibrary.myFunction(record, action);
}
```

**Do:**

```js
function (record, oldRecord, action) {
  app.myLibrary.myFunction(record, action.field('name').val(), action.field('age').val());
}
```

## Advantages

- Easier to test on dynamic console
- Editor autocomplete tells what parameters are needed

### Example

**myLibrary**

```js
exports.myFunction = function (user, name, age) {
  sys.logs.info('User is named: ' + name + ' and is ' + age ' years old');
}
