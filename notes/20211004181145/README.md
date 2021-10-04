# API Test: Postman Pre-Request Script

Found out that Postman allows you to use javascript before sending a
request. This would be so much valuable to test signature on PandaDoc
endpoint.

On `Pre-Request Script` tab you can append your code.

For PandaDoc I have to encrypt with `sha256` the raw body using a secret
webhooh shared key.

The script looks like:

```js
let sharedKey = 'SECRET_KEY_HERE';

// Postman have their own library to get data of request
let body = pm.request.body.raw;

// Postman also have CryptoJS library embedded
let signature = CryptoJS.HmacSHA256(body, sharedKey).toString();

// Set variable and then use it like query param with value: {{signature}}
pm.variables.set('signature', signature);
```
