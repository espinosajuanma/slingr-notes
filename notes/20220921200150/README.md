# Migrations tip `#1`

It is nice to disable `performValidations` on save to avoid broken
records errors.

Another useful option is the `triggerEvents` to avoid triggering
multiple data listeners. Only if we don't need those to run.

```js
sys.data.save(record, {
  performValidations: false,
  triggerEvents: false,
});
```

Make sure don't abuse this options and think pretty well all the
possible consequences.

