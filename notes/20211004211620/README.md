# Method `val()` of field type Date is a Date Object

There is no need to instantiate a Date object when you have a date type
field.

```js
var date = record.field('date').val();

log(date.getTime());
```
