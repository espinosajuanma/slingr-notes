# Hotfix: Add a group to user

If for some reason you can't edit your own profile and add the
«Developers» group to your user you can use this script.

```js
var user = sys.data.findOne('sys.users', {email: 'youremail@domain.com'});
sys.users.addGroup(user, 'developers', true);
sys.data.save(user);
log('Contains group: ' + sys.users.containsGroup(user, 'developers'));
```
