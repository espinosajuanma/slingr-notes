# Get current user Record with `sys.context`

Never used the context package. Today I have to set a permission of an
action and for that match one user record.

```js
function (record, parentField, action) {
  return sys.context.getCurrentUserRecord().id() == app.settings.getPayrollAccountant().id();
}
```

[Reference](https://slingr-stack.github.io/platform-docs/app_development_js_api_context.html#sys.context.getCurrentUserRecord)
