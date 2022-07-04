# Create users with the Javascript API

I had a problem trying to create a user with a custom password. This was
because the `sys.users` entity has some extra fields inside the nested
`authentication`.

- `authentication.passwordExpired` - Use true if need the final user to
  set his credentials again

The other fields to set a password are `newPassword`,
`passwordConfirmation` and `password`. The platform will handle the
encryption and protection of this plain data in the database.

```js
var user = sys.data.createRecord('sys.users');
user.field('email').val('smith@hello.com');
user.field('firstName').val('Jhon');
user.field('lastName').val('Smith');
user.field('groups').add({
  primary: true,
  group: 'admin'
});
user.field('authentication.generatePassword').val(false);
user.field('authentication.newPassword').val(password);
user.field('authentication.passwordConfirmation').val(password);
user.field('authentication.password').val(password);
user.field('authentication.passwordExpired').val(false);
```
