# Is `${APP_ENV}` stop using `${APP_DEV}`

This is just a note to my stupidity. I keep using the environment
variable `${APP_DEV}` like if is something, when I want to use the
`${APP_ENV}` variable which is the one that store the environment where
the app is running.

```js
log('We are using ${APP_NAME}-${APP_ENV}');
```
