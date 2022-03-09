# Query cursor timeout workaround

When we are managing big datasets and heavy processes with each record
we get from the database sometimes we are going to "run out" of time and
the platform will give us a `timeout` exception.

We can still do some things to avoid this.

```js
var BATCH_AMOUNT = 25; // Amount of records until we refresh the cursor

var cursorCount = 0;
function getCursor() {
  var cursor = sys.data.find('entityName', {
    status: 'notEquals(completed)'
  });
  sys.logs.info('Found ' + cursor.count());
  cursorCount = 0;
  return cursor;
}

var processed = 0;
var cursor = getCursor();
while(cursor.hasNext()) {
  processed++;
  cursorCount++;
  var record = cursor.next();
  log('Working on record ['+record.id()+']');
  
  // do stuff

  // update status to avoid re-query again
  record.field('status').val('completed');
  sys.data.save(record);

  if(cursorCount >= BATCH_AMOUNT) {
    sys.logs.info('Processed '+processed+' records');
    cursor = getCursor();
  }
}
```
