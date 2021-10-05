# Use environment variables for secrets

Normally you have to setup environment variables to keep your secrets.

External services usually provide a test environment or a SandBox. To
keep separated this we use environment variables.

So we can have different settings on `dev`, `staging` and `prod`
without fixing the field on every push.

Usage: `${VARIABLE_NAME}`

## Usage

Settings fields of endpoints isn't the only place where we can read
environment variables.

If needed it can be read anywhere, even on scripts:

```js
var mySecretKey = '${VARIABLE_NAME}';
log('Shh, your secret key is: ' + mySecretKey);
```

Also can be used on:

- Custom views
  - HTML
  - CSS
- Anywhere

## Monitor

Environment variables can be changed from builder and monitor too

> In general all things that are environment dependent it can be changed
> from the Monitor

## Keep in sync

The flag "Keep in sync" is used to share a variable from one environment
to other.

For example if we use the same variable in `dev` and `staging` we set
this to true.

But we keep it in false on `prod` and set another value. So if we make a
sync from `staging` to `prod` it shouldn't pass it because they are not
in sync.

