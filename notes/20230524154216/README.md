# Platform booleans are weird

If you expect to use the returning boolean from the JavaScript Slingr API within an if statement it is going to work fine.

```js
if (record.isNew()) {
  // record without an ID
}
```

But something weird happen when you try to use that same boolean like a returning value

```js
function (record) {
  return record.isNew();
}
```

In this case that operation, that could be a read/write access value for permissions is going to be always true. This is probably for some conversion with Rhino engine in Java and what returns is probably translated to an object or something which I don't know. But to be aware remember that is not going to work as a boolean returning that value (when the function expect a boolean).

## Solutions / Workarounds

Some solutions could be casting it to an actual JavaScript boolean.

```js
if (record.isNew()) return true;
return false;
```

```js
return Boolean(record.isNew());
```

```js
return !!record.isNew());
```
