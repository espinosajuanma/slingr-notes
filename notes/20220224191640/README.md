# Make a migration plan before remove a field

Well, I removed a field of an entity to make the same again. But when I
pushed this change all the old data of that fields disappear.

Sure, I forget that every field is a metadata, and as metadata they are
referred with an id. When I removed and created again I am not moving
data from one place to other, I am just erasing all data of the field I
deleted and just creating a new one with any data.

## Make a plan

Just like have a release with the new and old field at the same time.
With a migration script to move all old data field to the new one.

Or just screw it, like me. That I had to wrote a migration script to
store the old data in a JSON string before release. And then another
script to write from the JSON string to the new field. It is cumbersome
and not ideal, I know.
