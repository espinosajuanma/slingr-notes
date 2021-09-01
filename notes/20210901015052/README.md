# Looping 2 nested fields

I don't like this solution. But it is the better I could find to do this
job.

`System > Users > Notifications > Types`

- `Notifications` is a nested field that has:
    - `Category`
    - `Types` is a nested field that has:
        - `Type` which is a relation to entity `notifications.notificationTypes`
        - `Channels` which is a choice field

```js
var user = sys.data.findById('sys.users', '611bf51bc7a9120fa4c083a9');

var notifications = user.field('notifications');
var typeTimeTracking = sys.data.findOne('notifications.notificationTypes', { name: 'time-tracking-reminder' }); // findOne() => Trae un Record

notifications.each(function(notification){
  var types = notification.field('types');

  types.each(function(type) {
    if(type.field('type').id() == typeTimeTracking.id()) {
      type.field('channelsEnabled').val(null);
    }
  });
});
```
