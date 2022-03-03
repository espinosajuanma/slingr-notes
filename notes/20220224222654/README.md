# Always check `Monitor > Database` after a refactor

## TL;DR

Just check `Monitor > Database > Entities` to find broken indexes or
refresh relations.

## Details

Working a while with an entity I set an old field to be `unique` and so
`indexable`.

After pushing the changes I tried to run two processes at the same time.
This code created the records but the field value that supposed to be
unique they wasn't. I check and I had multiple entries with the same
values.

I thought it was a platform bug and I was ready to report it. Joe helped
me and told me that after this refactoring a job on the MongoDB instance
is trigger. Then we check the `Monitor > Database > Entities` and sure
the issue it was on my side.

The monitor show an error at indexes tab:

```
INFO

Could not add index [data.fieldName] in entity [entityName] because
there are duplicates: Write failed with error code 11000 and error
message 'E11000 duplicate key error collection:
app-dev.runtime.data.entityName index: data.fieldName dup key: {
data.fieldName: null }
```

This was telling me that it couldn't refactor thee database because or we
have null data or repeated values in old records.

## Fix it

1. Remove dupe data (Runtime)
1. Unset `unique` and `indexable` flags (Builder)
1. Push changes
1. Set `unique` flag to true
1. Push changes
1. Check `Monitor > Database > Entities`

This would re-trigger the database refactoring and successfully create
the index.

## Automatic refactoring

Read [Automatic
refactoring](https://platform-docs.slingr.io/app_development_automatic_refactorings.html)
at the platform docs.
