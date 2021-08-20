# Query builder

If need to find a list of records that have many conditions this is the
best way.

```js
var query = sys.data.createQuery('frontendBilling.projectServices').query(function(q) {
  return q.and(
    q.field('project').equals(record.field('project').id()),
    q.field('service').equals(field.id()),
    q.field('beginningOfServices').lessOrEquals(record.field('day').val()),
    q.or(
      q.field('endOfServices').empty(),
      q.field('endOfServices').greaterOrEquals(record.field('day').val())
    )
  );
});

var projectServices = sys.data.find(query);
```

The result of this query it will be a `resultSet` that could be
iterated.
