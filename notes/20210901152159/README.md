# «Choice» type field

Fields of choice type are arrays with strings inside.

```js
var choices = record.field('fieldName').val(); // ['item1', 'item2']
```

Array functions are pretty handy with this kind of field.

## Removing an item

```js
newChoices = choices.filter(function(choice) {
  return choice != 'item2';
});

record.field('fieldName').val(newChoices);
```

> Don't forget to use `save` and `lock` methods for change a record

## Adding an item

```js
choices.push('item2');

record.field('fieldName').val(choices);
```

> Don't forget to use `save` and `lock` methods for change a record
