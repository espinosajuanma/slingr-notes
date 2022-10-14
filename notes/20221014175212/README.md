# "Access forbidden for specified field value" on new record POST API request

Today I had this issue with a relationship field when I tried to create
a record with the API Rest.

```json
  errors: [
    {
      field: 'contactFlow',
      fieldLabel: 'Contact Flow',
      code: 'invalid',
      message: 'Access forbidden for specified field value',
      additionalInfo: [Object],
      params: []
    }
  ]
```

When I checked the permissions of that specified field, for my surprise,
the group user was able to read and write. So I didn't understand why
the error said it didn't have permissions.

So the issue was that the group user haven't access permissions to the
related entity. Once I fixed that the issue was resolved.
