# Fastest way to create a `copy` action

```js
exports.copyRecord = (record, viewId) => {
  let entityName = record.entityName();
  let newRecord = sys.data.createRecord(entityName);
  newRecord.fromJson(record.toJson());
  newRecord = sys.data.save(newRecord);
  if (viewId) {
    sys.ui.sendMessage({
      scope: 'global',
      name: 'navigate',
      view: viewId,
      recordId: newRecord.id()
    });
  }
}
```
