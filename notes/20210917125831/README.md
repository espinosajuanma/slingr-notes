# Date field conditional. Cumbersome...

I asked the guys of the platform why `.equals()` is not working as
intended on Date type wrappers.

There is another not so much cumbersome way to make this conditional.
But is the same, is not like to have a `record.field('dateField)
.equals(new Date())`. It would look so much cleaner and intuitive.

```js
record.field('dateField').format() === new Date().toISOString().substring(0,10)
// true
```
