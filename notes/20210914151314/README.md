# Compare date fields with today

Setting a date to midnight it is the way to know if a date is equals to
other. Date fields save the dates and compare in this hour.

```js
// Set the date to 00:00:00 so you can compare later with a date field
var today = new Date(new Date().setHours(0, 0, 0, 0));

var query = sys.data.createQuery('management.workAgreements')
    .query(function(q) {
        return q.or(
          q.and(
            q.field('startDate').lessOrEquals(today),
            q.field('status').equals('pending')
          ),
          q.and(
            q.field('endDate').lessOrEquals(today),
            q.field('status').equals('active')
          )
      );
    });
```
