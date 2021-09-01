# Using `.lock()` with a callback

Always we edit a record we should use the `.lock()` function.

> This callback function is executed after the lock is acquired
> successfully. The acquired lock is released automatically after the
> execution of defined callback.

[Reference](https://slingr-stack.github.io/platform/app_development_js_api_data.html#sys.data.Record.lock_callback)

```js
var person = sys.data.findById('sys.users', '611bf51bc7a9120fa4c083a9');

person.lock(function(person){
  person.field('notifications').each(function(notification){
    notification.field('types').each(function(type){
      if(type.field('type').label() == 'time-tracking-reminder'){
        var channels = type.field('channelsEnabled').val();
        var newChannels = channels.filter(function(channel){
          return channel != 'slack';
        });
        type.field('channelsEnabled').val(newChannels);
      }
    });
  });
  sys.data.save(person);
});
```
