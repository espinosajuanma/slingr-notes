# Get record created time parsing it from the id

@`Juan Espeche` show us this cool trick with @`Seba Moyano` help.

It is a tricky but effective way to get the created time of any id from
MongoDB.

```js
var user = sys.data.findOne('sys.users', { email: 'jespeche@slingr.io' });

var time = parseInt(user.id().substr(0,8), 16)*1000;
var createdAt = new Date(time);
```

I mean, we can just create a field with a default value. But this is
beyond that. If we make this field on a late stage of our application
there is no way to know the date of the oldest records. With this trick
we can make a migration script to recover that data.

Also, if we want to be cheap with the amount of data we store on the
database we just can include those lines whenever we need to use it.
(Don't be this guy)


