# REST API - Use `version` attribute with `PUT` method

Using this version attribute the API will throw an "Optimistic locking
exception" if the record was updated at the same time for other user.

> **Platform-docs:** Optimistic locking exception. This happens when
> two users tries to update the same record at the same time. The once
> that enters in the second place will get this error.

The HTTP error code will be a `409`.

```sh
curl -s -X PUT https://app-name.slingrs.io/dev/runtime/api/entityName/$id \
  -H 'Content-Type: application/json' \
  -H "token: $token" \
  -d '{ "version": 2, "field": "new value" }'
```

Also like a side note, there is no need to send all the fields and
values of the record. You can just send the fields you want to update.
