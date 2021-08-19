# Iterate a `sys.commons.ResultSet`

Using the method `.find()` from package `sys.data` will return a
`ResultSet`.

This can be iterated with the methods `.hasNext()` and `.next()` in a
while loop.

```js
// Returns a ResultSet
var services = sys.data.find('project.services', { project: project.id() });

log('Amount of services: ' + services.count());

while(services.hasNext()) {
  var service = services.next();
  log(service.label());
}
```

> In this `ResultSet` has `sys.data.Record` objects
