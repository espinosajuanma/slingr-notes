# Custom view local development

Working with custom views can be a really painful process if we have to
tweak little stuff and push changes to the slingr app.

So it is important To have a local development environment.

To achieve this we are going to adapt the
[website-utils](https://github.com/slingr-stack/website-utils) library.

## Steps

1. Create a directory to save your HTML, CSS and JS files
1. Add the `slingr-ws.js` file
1. Refer the file in your HTML with a `<script src="./slingr-ws.js">` tag
1. Open a browser-sync local server to reload the website at file change
1. Append `token`, `app`, and `env` to the query parameters:
    - `?token=YOUR_TOKEN&app=APP&env=dev`

## Token

The "easiest" way to get a token is using the curl command

```sh
curl -X POST https://APP.slingrs.io/dev/runtime/api/auth/login \
  -H 'Content-Type: application/json' \
  -d '{"email": "youremail@example.com", "password": "your_password"}'
```

But also can be seen in all slingr requests in the header `token: the_token`

## Web utils file

The modifications to the library are:

```js
let address = window.location.search;
let params = new URLSearchParams(address);
let app = params.get('app');
let env = params.get('env');

slingr.ws.TOKEN = params.get('token');
slingr.ws.API_URL = `https://${app}.slingrs.io/${env}/runtime/api`;
```

At the end set the variable `sys` to the slingr object so we can use
`sys` like a normal custom view development.

```js
var sys = slingr;
```

## TO DO

- [ ] Replace environment variables like `{APP_URL}`
