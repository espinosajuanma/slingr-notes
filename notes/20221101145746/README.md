# Use `sys.data.delete()` to remove records with a query

To remove records I usually make a query and then iterate each one to
remove it. This could bring some issues with the iteration and
pagination.

```js
let records = sys.data.find('entityName', { shouldRemove: true });
while (records.hasNext()) {
  let record = records.next();
  sys.data.remove(record);
}
```

So the way we can solve this is using actually the `delete` method.

```js
sys.data.delete('entityName', { shouldRemove: true });
```

This spawns a job and returns the job `id` if for some reason we need to
wait until is done.
