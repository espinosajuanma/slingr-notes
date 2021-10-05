# Custom event data

We can't send a Record or a ResultSet like data of a custom event.

But we can send anything that is serializable or convert to JSON format.

```js
sys.events.triggerEvent('contractSigned', {
  contractId: contract.id(), // Send id, not the record
  documentData: res.data, // Object can be JSON stringifyble
});
```
