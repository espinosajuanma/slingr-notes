# Actions: return as response

Use the flag `return as response` to return a js object.

Be careful on which scope to use the return keyword. Don't use it inside
a callback as inside a `.lock()`

🛇  Bad one:

```js
record.lock(function (record) {
  // do stuff
  sys.data.save(record);
  return { success: true };
});
```

👍 Good one:

```js
record.lock(function (record) {
  // do stuff
  sys.data.save(record);
});
return { success: true };
```

