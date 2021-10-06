# Execute action from script

Really useful for focus testing on small things that require a lot of
steps on app.

`myRecord.action('actionName', { oneParam: 'valueOfParam' });`

Real example:

```js
var p = sys.data.findOne('management.payrollRun', {
  status: 'pending'
});

p.action('sendPaymentDocuments');
```
