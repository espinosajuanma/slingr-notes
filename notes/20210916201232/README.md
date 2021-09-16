# Init a custom view

Quick tip when init a new custom view:

```js
var RootModel = function() {
  var self = this;

  self.currentUserID = ko.observable();

  self.onImportHours = function() {
    // to do
  }

  return self;
}
```

This resolves the problem with `this` keyword on different scopes.
Also allows a better way to work as a OOP design.
