# Save a `File` field

To save a file in a field you can just referenced to the fileId.

```js
var file = app.endpoints.pandadoc.downloadDocument(res.data.id,
contract.label());

contract.lock(function(record) {
  record.field('signedDocument').val(file.fileId);
  sys.data.save(record);
});
```
