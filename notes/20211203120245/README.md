# Use markdown and `.text()` for URL fields

The value off an URL field could be just an URL, but also we can use
markdown to make it more "pretty".

- `(URL_LINK_HERE)[Text of link here)`

If we want to get the text instead the full value of the field we can
use `.text()`.

```js
var myRecord = sys.data.findOne('entityName', {
  name: 'My record'
});

log(myRecord.field('urlFieldName').text());
```
