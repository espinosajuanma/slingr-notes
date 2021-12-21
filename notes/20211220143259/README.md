# Endpoints - Use quotes for `mvn` commands on PowerShell

We had some issues running the `mvn exec:java` command on powershell.

PowerShell is picky. So remember to add quotes to wrap the different
arguments.

```
mvn package exec:java "-Dexec.mainClass=io.slingr.endpoints.mandrill.Runner" "-Dexec.args=configurationFile=endpoint_proxy.properties" -DROOT_LOGGER=stdout
```
