# `HQ` - Update Notifications (in prod) if created a `Notification Type`

Next time I work on a Notification Type for HQ, I have to make sure to
update the notifications and add to production notes that this is need
it.

```js
var users = sys.data.find('sys.users', {
  status: 'ACTIVE'
});

while (users.hasNext()) {
  var user = users.next();
  try {
    app.notifications.updateNotification(user);
  } catch (e) {
    log(user.label() + ' - ' + e.message);
  }
}
```
