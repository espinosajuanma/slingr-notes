# You can get endpoint information with `sys.endpoints`

> Note: Endpoints in the future will not be endpoints itself. But they
> will be a combination of packages and services. We will have to look
> this library change when they become services.

This is actually in the documentation but I always overlook.

You can find an endpoint by its name or id using the helpers:

- `sys.endpoints.findByName()`
- `sys.endpoints.findById()`

```js
let endpoint = sys.endpoints.findByName('pandadoc');
sys.logs.info(endpoint.label());
```

## Endpoint Class

The `Endpoint` entity has some useful information:

- `endpoint.id()` - Returns the id of the endpoint
- `endpoint.label()` - Returns the label of the endpoint
- `endpoint.name()` - Returns the name of the endpoint
- `endpoint.type()` - Returns the type of the endpoint
  - On my tests it returns the name of the endpoint...
- `endpoint.status()` - Returns the status of the endpoint
  - `DEPLOYED`, `UNDEPLOYED`, `DEPLOYING`, `UNDEPLOYING`, `UNKNOWN`
- `endpoint.version()` - Returns the version of the endpoint

## Is Deployed

The library `sys.endpoints` also has a helper that returns a boolean if
the endpoint is deployed or not.

```js
let working = sys.endpoints.isDeployed('pandadoc');
if (! working) {
  sys.logs.warn(`Endpoint [pandadoc] is not deployed at this moment`);
}
```
