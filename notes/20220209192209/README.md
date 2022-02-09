# Use `@config.field` or `config.field` the good way on endpoints configurations

If you want to pass just the value use `@`. In this case `otherField`
value is `true` or `false`.

```json
{
    "label": "Field",
    "name": "field",
    "type": "password",
    "multiplicity": "one",
    "required": true,
    "visibility": "@config.otherField",
    "showLabel": true,
    "defaultValue": "12345678",
    "typeOptions": {}
}
```

Instead if you need to retrieve a boolean through an expression do not
use it. In this case the field will be visible if `otherField` has the
value `myValue`

```json
{
    "label": "Field",
    "name": "field",
    "type": "password",
    "multiplicity": "one",
    "required": true,
    "visibility": "config.otherField == 'myValue'",
    "showLabel": true,
    "defaultValue": "12345678",
    "typeOptions": {}
}
```
