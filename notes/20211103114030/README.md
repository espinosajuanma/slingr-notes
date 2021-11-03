# Impersonate an user through a script

Sometimes when we create a record with an script and this have a field
`createdBy` with default value `sys.context.getCurrentUserRecord()` this
automatically save the user as the system user.

To avoid this to happen, Juan Guardiola show me that we can use this
function to impersonate someone:

```js
var user = sys.data.findOne('sys.users', {'slack.userId': event.data.user.id});
sys.context.setCurrentUserRecordById(user.id());
if (user) {
  // create the record
} else {
  // send error message
}
```
