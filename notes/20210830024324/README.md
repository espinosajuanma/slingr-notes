# Updating an endpoint

[Reference](https://slingr-stack.github.io/platform/extensions_java_sdk.html)

## Requisites

- Java installed and environment variables: `JAVA_HOME` and `JRE_HOME`
- Maven installed
- Git bash installed
- ngrok installed
- A code editor software

## Setting up the project

Look for the SLINGR GitHub endpoint repository.

Run this commands:

```
git clone https://www.github.com/slingr-stack/endpoint-repository
cd endpoint-repository
git branch new-branch-name
git checkout new-branch-name
mvn clean package
```

## Working on

### `endpoint.json`

This is a file for add and set configurations options for.

### Java Main file

...

### Scripts file

...

## Testing and debugging

### `endpoint_proxy.properties`

```yml
_endpoint_name=proxy
_app_name=yourtestapp
_environment=dev
_pod_id=id
_profile=default
_custom_domain=
_debug=true
_local_deployment=true
_base_domain=slingrs.io
_webservices_port=10000
_endpoints_services_api=https://yourtestapp.slingrs.io/dev/endpoints/proxy/api
_token=91833a8b-929f-4eab-b7b4-2383c10cd629
_endpoint_config={"token":"123456"}
```

### Running the endpoint locally

`mvn exec:java -Dexec.mainClass="io.slingr.endpoints.skeleton.Runner"
-Dexec.args="configurationFile=endpoint_proxy.properties"
-DROOT_LOGGER=stdout`

### Proxy

Using ngrok...

`ngrok http 10000`

Output will give you an URL to use at the platform as your Proxy
endpoint.

```
...
```

### Platform

```js
var res = app.endpoints.proxy.get('/url');
log('res: ' + JSON.stringify(res));
```

