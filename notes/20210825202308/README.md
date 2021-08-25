# Using `.lock()` and `.unlock()`

When using `sys.data.lock(record)` I should use `.unlock(record)` when I
finish the manipulation.

But the lock method and other methods could cause a throw exception. For
this I have to make sure I use a try/catch blocks. So in finally block I
run `sys.data.unlock(record)` even when an exception was thrown.


```js
function (record, oldRecord, action) {
  try {
    sys.data.lock(record);
    record.field('status').val('inProgress');
    record.field('notes').add({
      note: action.field('note').val()
    });
    sys.data.save(record);
  } catch(e) {
    sys.logs.error('Ups! Something wrong happend!', e);
  } finally {
    sys.data.unlock(record);
  }
}
```
