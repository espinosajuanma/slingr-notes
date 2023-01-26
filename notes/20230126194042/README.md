# Aggregate Queries for the win!

## Issue

We have an entity with a multi-nested field and we need to get the
records that has the next conditions:

- `nestedField.fieldA` is `true`
- `nestedField.fieldB` is `false`

With a normal query we could do something like this:

```js
let resultSet = sys.data.find('entity', { 'nestedField.fieldA': true, 'nested.fieldB': false });
```

The problem is that this query will not considered that the field
matches in the same nested field. So it can fetch a record that has this
structure in the nested field:

```json
[
  { "fieldA": true, "fieldB": true },
  { "fieldA": false, "fieldB": false }
]
```

As you can see it brings a record that has both conditions, but these
doesn't apply to the same nested object.

## Solution

Use aggregate queries!

Aggregate queries are a great tool working with MongoDB.

In this case, use `unwind` operation will

```js
let resultSet = sys.data.aggregate('support.tickets', [
  { unwind: { fieldPath: 'nestedField' } },
  { match: { 'nestedField.fieldA': true, 'nestedField.fieldB': false } },
]);
```

## Caveats

- Unwind will create one result item for each nested
  - It can create duplicate if multiple nested comply with the condition
  - It remove all other nested fields as if the item has only one
- It will not return a `Record` object
  - Each item is a literal object. To access a field use dot notation.

## Workarounds

### Missing nested fields

If you need the whole information of the nested field you may want to
use `project` operation to get minimal information and then do a find
with the results ids.

### Duplicate records

Use `group` operation, or handle it with javascript.
