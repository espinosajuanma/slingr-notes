# Use `sys.context.any()` to check in which context the code is running

This is not usual, and maybe you never need it. But it is a great trick
to have under our sleeves.

If you have a helper function in a library and you call it from
different contexts you can change the behaviour of the function based on
the context.

```js
exports.mySpecialFunction = function () {
  let isMySpecialListener = sys.context.any().listener('mySpecialListener').check();
  if (isMySpecialListener) {
    // do something
  } else {
    let isMySpecialAction = sys.context.any().entity('myEntity').action('mySpecialAction').check();
    if (isMySpecialAction) {
      // do something else
    }
  }
}
```

[https://platform-docs.slingr.io/app_development_js_api_context.html#sys.context.any](Slingr Docs)
