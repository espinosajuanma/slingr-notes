# Use `/data/{entityName}/{recordId}/files/{fileId}` instead `/files/{id}`

If we want to get sure we are getting the right permissions to download
a file we should use the entity path to the API.

Files do not have permissions.

```
Downloading files
GET /files/{id}
Downloads a file. This service is only available for developer and system users.
```

Using the next path it will download the file checking the entity access
permissions first.

```
Downloading record files
GET /data/{entityName}/{recordId}/files/{fileId}
Downloads a file that belongs to a specific record. User permissions check is performed.
```
