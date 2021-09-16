# Add `return`to Default Value Scripts

I was wondering why my Default Value scripts wasn't working.

So I realized that I should **always** return the value.

```js
function (record, parentField, action) {
  return record.field('amount').val();
}
```
