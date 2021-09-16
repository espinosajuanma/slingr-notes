# Action with Linked Parameters

When you need to add an action and add a parameter of the same entity
and fill it with the current value you can use a linked parameter.

In other way you would have to add a Default Value script as:

```js
return record.field('thisField').val();
```

But this is not need it with linked parameters.

Also if you want to update this fields you don't need to write an
action at all if you use the option on Action: `Save linked
parameters`.
