# Understanding `sys.data.Record.history()` for history logs

We were checking out the class `sys.data.RecordHistoryLogs` in the
documentation and it is pretty straight forward.


## Getting the latest change

The method `lastModifiedLog()` returns `null` or the latest log change
with event `USER_RECORD_CHANGE`.

```js
let record = sys.data.findOne('settings');
let history = record.history();
let latest = history.lastModifiedLog();
```

## Finding a change

But you can also get a list of them using the `find(options)` method.

```js
let record = sys.data.findOne('settings');
let history = record.history();

let changes = history.find({ size: 10, eventType: 'USER_ACTION_PERFORMED' });
```

This returns an array ordered from newest to oldest change. The filters
could be: `eventType`, `from`, `to`, `size`, `offset`.

## The `sys.data.RecordHistoryLog` class

- `id()` - Returns the id of the log
- `timestamp()` - Returns a string UTC date ISODate
  - `2022-12-22T18:23:34.145Z`
- `eventCategory()` - Returns the category of the log
  - `USER_RECORD_CREATED`
  - `USER_RECORD_CHANGED`
  - `USER_RECORD_DELETED`
  - `USER_ACTION_PERFORMED`
  - `SCRIPT_RECORD_CREATED`
  - `SCRIPT_RECORD_CHANGED`
  - `SCRIPT_RECORD_DELETED`
  - `SCRIPT_ACTION_PERFORMED`
  - `SYSTEM_CASCADE_UPDATE`
  - `SYSTEM_REFACTORING`
- `user()` - Returns the email of the user who made the change
- `ip()` - Returns the ip when the log was created
- `oldRecord()` - Returns the old values of the fields
- `newRecord()` - Returns the new values of the fields

## Old Record - New Record

This two methods returns an object with the proper fields that were
changed and the old and new values depending the method you use.

```js
let record = sys.data.findOne('settings');
let history = record.history();
let latest = history.lastModifiedLog();
let newRecord = latest.newRecord(); // Array with new changes
let oldRecord = latest.oldRecord(); // Array with old changes

for (let index in newRecord) {
  let new = newRecord[index];
  let old = oldRecord[index];

  log(`Field [${new.fieldLabel}] New Value [${new.json}]`);
  log(`Field [${old.fieldLabel}] Old Value [${old.json}]`);

}
```

## Possible ideas

- Action to restore a previous state record
- List changes after one month and create an auditory report
