# Query `many-nested` fields as a pro...

I feel dumb saying that in the title. Working over one year and half
with Slingr and never realizing this.

In my latest note I talked about aggregate queries to match a
multi-nested value... Well this is nonsense. I mean we can do the same
without so much overhead.

The right solution is to actually use an structure to make sense the
nested to match the condition.

## Query map

```js
let rs = sys.data.count('testEntity', {
  nestedField: {
    fieldA: true,
    fieldB: false
  }
});
```

## REST API

```
GET /api/data/testEntity?nestedField={"fieldA":true,"fieldB":false}
```

## Do not do this

This matches the conditions individually.

```js
let rs = sys.data.count('testEntity', {
  'nestedField.fieldA': true,
  'nestedField.fieldB': false
});
```

So it can match a record with this nested structure:

```json
[
  {
    "fieldA": true,
    "fieldB": true
  },
  {
    "fieldA": false,
    "fieldB": false
  }
]
```
