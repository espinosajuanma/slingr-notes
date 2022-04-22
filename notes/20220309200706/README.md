# Field type: `Dynamic choice`

Load the data you need in a `default value` script.

```js
var data = sys.data.find('projects', {
  status: 'active'
});

var options = data.toArray().map(function (record) {
  return {
    label: record.label(),
    name: record.id() // It is going to be the value of the choice
  }
});

return {
  options: options,
  selectedValue: options[0].name
}
```

> Note: it broke if we use a view event like `on record change`. Make
> sure you use it with the `default value` or `before show` event.

Remember to use `selectedValue()` instead of `val()` to get the correct
value of field.

Another methods of this wrapper:

- `selectedLabel()`
- `options()`

[Documentation](https://platform-docs.slingr.io/app_development_type_dynamic_choice.html)
