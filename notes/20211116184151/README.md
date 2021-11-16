# Use `record.copy()` to clone a record

If for some reason you need to create a record really similar to another
one you can use the method `copy()`.

```js
var some = sys.data.createRecord('ticket');
some.field('name').val('Something nice');
some.field('category').val('new');
sys.data.save(some);

var other = some.copy();
other.field('category').val('old');
sys.data.save(other);
```
