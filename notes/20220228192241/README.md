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

> If the field version is not sent, then no version control will be done
> and you might end up overwriting changes from other users, so it is
> strongly recommended to use it when updating records.

[Ref](https://platform-docs.slingr.io/app_development_apps_rest_api.html#optimistic-locking)

Also like a side note, there is no need to send all the fields and
values of the record. You can just send the fields you want to update.
