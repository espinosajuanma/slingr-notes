# Query with `sys.ws.get()` using website-utils

I got used to write the queries to the REST API just using URL encoded
parameters: `?someField=someValue`, which is ok for a simple query or
just for quick prototyping.

But I forget that using the website utils library instead of sending a
string (the url) I can send an object with the url and the parameters as
two attributes:

## URL String

```js
sys.ws.get('/data/entityName?someField=someValue', callback);

function callback(data) {
  console.log(data);
}
```

## JS Object

```js
sys.ws.get({
  url: '/data/entityName',
  params: {
    someField: 'someValue'
  }
}, callback);

function callback(data) {
  console.log(data);
}
```

It may be a little bit more verbose, but could be easier to read when
you have a bunch of fields to filter. Also, the editor highlight helps a
lot with that.
