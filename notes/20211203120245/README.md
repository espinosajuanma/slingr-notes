# Use `(link)<label>` for URL fields

The value off an URL field could be just an URL, but also we can use
markdown to make it more "readable".

- `(URL_LINK_HERE)<Label for link>`

If we want to get the label instead the full value of the field we can
use `.text()`.

But if we just want the link we can use `.url()`.

```js
var myRecord = sys.data.findOne('entityName', {
  name: 'My record'
});

log('Label: ' + myRecord.field('urlFieldName').text());
log('URL:   ' + myRecord.field('urlFieldName').url());
```
