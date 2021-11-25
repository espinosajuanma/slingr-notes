# Use `record.isNew()` to limit permissions when create or edit records

If for some reason you need to allow write permissions of a field when
the record is being created, but not allow it for edit this record, you
can use `record.isNew()`.

This returns true if the record is not saved yet.
