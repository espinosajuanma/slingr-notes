# Comparing dates

`record.field('day')` is not the same as `record.field('day').val()`

```js
var date = record.field('day');

var query = sys.data.createQuery('entityNamePath').query(function(q) {
  return q.and(
    q.field('start').lessOrEquals(date.val()),
    q.field('end').greaterOrEquals(date.val())
  );
});

var result = sys.data.find(query);
```

[Query
dates](https://slingr-stack.github.io/platform/app_development_type_date.html#available-operators)
