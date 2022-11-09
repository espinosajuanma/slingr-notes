# REST API: Use param `_relationshipsToFetch` to get the relation document

This parameter is a comma separated list of the relationship field names
that we want to populate too.

```bash
curl https://{appName}.slingr.io/{env}/rutime/api/data/{entityName}?_relationshipsToFetch={relationshipFieldName} \
  -H 'Content-Type: application/json' \
  -H 'token: {token}'
```

Result:

```json
{
  "total": 1,
  "items": [
    {
      "id": "123",
      "version": 1,
      "label": "My Record",
      "someRelationship": {
        "id": "321",
        "label": "My other record",
        "fieldA": "valueA",
        "fieldB": "valueB",
        "fieldC": "valueC",
        "fieldD": "valueD"
      },
      "someOtherField": "other value"
    }
  ]
}
```
