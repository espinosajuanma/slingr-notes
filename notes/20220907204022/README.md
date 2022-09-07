# Handle inheritance actions

If we have a child entity from other parent entity we can't override an
action. So we need to do it with a handler.

Both parent and child entity could have this code in the same action:

```js
function (record, oldRecord, action) {
  app.libraryName.callAction(record);
}
```

And then the library could have a handler like this:

**libraryName**

```js
exports.callAction = function (record) {
  app[record.entityName()].callAction(record);
};
```

And then for each parent and child entity setup the functions in their
own libraries.

**parentEntity**

```js
exports.callAction = function (record) {
  // Do something in the parent entity record
};
```

**childEntity**

```js
exports.callAction = function (record) {
  // Do something in the child entity record
};
```
