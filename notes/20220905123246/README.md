# Calculated fields are processed before open Action View

I had weird log error in the monitor always I open any kind of view of
a global or record action.

```
» 2022-09-05 09:35:23.598 ERROR jmespinosa@slingr.io [NaN] is not a valid Decimal expression
```

The log error is not helpful at all. After reviewing +50 fields of this
entity I found out that I set an script for "Value Calculation" when I
intended to do it in "Read/Write Access".

I was returning a Boolean for the "Read/Write Access" script, but for
mistake I set it in the "Value Calculation" which was expecting a
number resulting in that error.

Going to make a ticket and hopefully the platform make a better error
logging to know faster where is the error. Anyway my learning for today
is:

> Calculated fields are processed every time we open an action view of
> that entity
