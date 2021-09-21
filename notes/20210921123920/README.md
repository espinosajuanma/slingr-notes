# Custom event with `sys.events.triggerEvent()`

Sometimes you need a script send a custom event. This are the steps to
set one.

## Call the event

Use this method when you want to trigger the event

```js
sys.events.triggerEvent('nameEvent', { name: 'Juanma' });
```

## Listen the event

- Create a new listener
- Use `Custom` as Type
- Add event with the name you used: `nameEvent`
- Fill the script with the action

```js
function (event) {
  var name = event.customData.name,
  sys.logs.error('Triggered event with data: [' + name + ']');
}
```

Output: `Triggered event with data: [Juanma]`
