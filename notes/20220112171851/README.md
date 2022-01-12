# Permissions - Difference between `values`, `user field`, `user value`

## Values

- List of fields of the entity
- Compare with a value

> Use it when you want just to check if a value of the entity is
> something

For example: If Configurations entity you want to check that the record
`active` boolean field is true.

## User Field

- List entity fields 
- Select a field relationship to `sys.users`
- Can use `Current Record`

> Useful when you need to check if the current user is included on an
> entity field

For example: In Ticket entity you want to check that user is listed on
`assignees` or is the same as `createdBy`.

## User Values

- List of `sys.users` entity fields
- Compare with a value

> Use it when you want to check if a value of the user is something

For example: In Contracts entity you want to check that user has
`contractManager` boolean field in true.
