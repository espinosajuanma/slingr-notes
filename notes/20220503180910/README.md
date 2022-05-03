# Use `forceUnlock(key)` to clean a locked key

We came across to a execution that stop running in the middle of a lock
and never released.

So we had to use this method to get rid of that lock:

```js
var recordId = 'xxxxxxxxxxxxxxxxxxxxx';
sys.utils.concurrency.forceUnlock(recordId);
```
