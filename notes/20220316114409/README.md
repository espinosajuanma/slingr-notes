# Use `sys.exceptions` to send custom HTTP errors

Sometimes we add a global action or any kind of action with the flag
`Result as response` to use with the REST API.

Now we can send custom HTTP error codes using the library exceptions.

```js
// Throw 404: notFound
sys.exceptions.throwException(sys.exceptions.NOT_FOUND_ERROR, 'Nothing to see here');
```

```sh
curl -iX PUT https://app.slingrs.io/dev/runtime/api/data/entity/action -H 'token: tokenvalue'
```

## The codes

[`sys.exceptions` error constants list](/notes/20220316120321/README.md)
