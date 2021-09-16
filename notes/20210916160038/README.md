# Don't forget to save Record after editing fields values

A common mistake I am doing is to forget use `sys.data.save(record);`
when I finish editing a record.

```js
compensation.lock(function(record) {
  record.field('status').val('discarded');
  sys.data.save(record);
});
