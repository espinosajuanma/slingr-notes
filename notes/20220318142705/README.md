# Clear the app cache without accessing the platform manager

```sh
curl -X PUT "https://$APP.slingrs.io/$ENV/runtime/api/system/clearCache" -H "token: $TOKEN"
```
