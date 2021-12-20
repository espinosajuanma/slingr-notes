# Use `.empty()` and not `isEmpty()` on complex queries

Just a reminder that query operators on complex queries aren't the same
than wrapper conditions methods.

```js
var query = sys.data.createQuery('entityName').query(function(q) {
  return q.and(
    q.field('template').empty()
  );
});
```

On normal if condition

```js
if (record.field('template').isEmpty()) {
  // do something
}
```
