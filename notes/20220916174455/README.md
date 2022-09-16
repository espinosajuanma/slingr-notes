# Query file fields by `name` or `id`

This type of field is really different to others. At first as the
files has a name and an id I thought these were like any other
relationship files. But no, to query them you have to do a tricky stuff.

Anyway, the documentation is clear in how to create a query to find a
reference to a file.

```js
let records = sys.data.find('tasks', { attachments: 'like(file.png)' });
```

Use `like()` operator to find by name. Sometimes the file names are
updated to store the size of the file.

To find by file id we have to access the `id` attribute of the file
field.

```js
let records = sys.data.find('tasks', { 'attachments.id': '1234' });
```

