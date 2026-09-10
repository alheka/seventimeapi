# Documents
## Get Documents

Documents are included when fetching other objects, e.g. work orders or projects. They are found in an array named documents. The objects in the array contain a path which can be used to download the documents. Folders are also included and will have the flag isFolder as true.

Documents can also be fetched directly from the Documents API. A document belongs to either:

- an entity, using `entityId` and `entityType`, e.g. a work order or project
- a document list, using `documentListId`, e.g. the general document archive

> Fetching a work order returns a documents array like this:

```json
{
  "data": {
    "documents": [
      {
        "createDate": "2021-08-24T11:40:16.285Z",
        "modifiedDate": "2021-08-24T11:40:16.285Z",
        "_id": "6124daa00c1532914b92",
        "name": "plan1.pdf",
        "path": "https://seventimedev.s3-eu-west-1.amazonaws.com/...",
        "contentType": "application/pdf",
        "size": 20548,
        "user": "571f61330c7f498a2d5812",
        "userName": "Anna Andersson",
        "isLink": false,
        "isFolder": false,
        "folderId": "6124d18c910273b259cf819",
        "isPublic": false
      }
    ]
  }
}
```

```shell
curl "https://app.seventime.se/api/2/documents?entityId=5bae34dca878b5497748&entityType=200" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/documents?entityId=5bae34dca878b5497748&entityType=200";
let options = {
  url: url,
  headers: {
    "Client-Secret": "thisismysecretkey",
    "Content-Type": "application/json",
    "Accept": 'application/json'
  }
};

request(options, function(error, response, body) {
  if (!error && response.statusCode == 200) {
    let info = JSON.parse(body);
    // ...
  } else {
    console.error("Error when calling API! HTTP Code: " + response.statusCode + ", Error message: " + body.errorMessage);
  }
});
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "createDate": "2021-08-24T11:40:16.285Z",
      "modifiedDate": "2021-08-24T11:40:16.285Z",
      "_id": "6124daa00c1532914b92",
      "name": "plan1.pdf",
      "path": "https://seventimedev.s3-eu-west-1.amazonaws.com/...",
      "realPath": "1234/workOrders/5bae34dca878b5497748/20210824134016/plan1.pdf",
      "contentType": "application/pdf",
      "size": 20548,
      "user": "571f61330c7f498a2d5812",
      "userName": "Anna Andersson",
      "isLink": false,
      "isFolder": false,
      "folderId": null,
      "isPublic": false
    }
  ]
}
```

This endpoint retrieves documents for an entity or for a document list.

### HTTP Request

`GET https://app.seventime.se/api/2/documents`

### Query Parameters

Parameter | Required? | Description
--------- | --------- | -----------
entityId           | Yes* | Id of the parent object, e.g. id of a work order.
entityType         | Yes* | Entity type of the parent. See table below for available types and corresponding code.
documentListId     | Yes* | Id of the document list. Used for documents in the general document archive.
folderId           | No | Folder id. Only used together with `documentListId`. Defaults to `null`, which returns documents and folders in the root of the document list.

*Either `entityId` + `entityType` or `documentListId` is required. They cannot be combined.

## Get a specific Document

```shell
curl "https://app.seventime.se/api/2/documents/6124daa00c1532914b92?entityId=5bae34dca878b5497748&entityType=200" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/documents/6124daa00c1532914b92?entityId=5bae34dca878b5497748&entityType=200";
let options = {
  url: url,
  headers: {
    "Client-Secret": "thisismysecretkey",
    "Content-Type": "application/json",
    "Accept": 'application/json'
  }
};

request(options, function(error, response, body) {
  if (!error && response.statusCode == 200) {
    let info = JSON.parse(body);
    // ...
  } else {
    console.error("Error when calling API! HTTP Code: " + response.statusCode + ", Error message: " + body.errorMessage);
  }
});
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "createDate": "2021-08-24T11:40:16.285Z",
    "modifiedDate": "2021-08-24T11:40:16.285Z",
    "_id": "6124daa00c1532914b92",
    "name": "plan1.pdf",
    "path": "https://seventimedev.s3-eu-west-1.amazonaws.com/...",
    "realPath": "1234/workOrders/5bae34dca878b5497748/20210824134016/plan1.pdf",
    "contentType": "application/pdf",
    "size": 20548,
    "user": "571f61330c7f498a2d5812",
    "userName": "Anna Andersson",
    "isLink": false,
    "isFolder": false,
    "folderId": null,
    "isPublic": false
  }
}
```

This endpoint retrieves a specific document. For documents attached to an entity, include `entityId` and `entityType` as query parameters. For documents in a document list, only the document id is required.

### HTTP Request

`GET https://app.seventime.se/api/2/documents/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the document to retrieve

### Query Parameters

Parameter | Required? | Description
--------- | --------- | -----------
entityId           | Yes* | Id of the parent object for documents attached to an entity.
entityType         | Yes* | Entity type of the parent for documents attached to an entity.

*Required only when the document is attached to an entity.

## Get Document Lists

```shell
curl "https://app.seventime.se/api/2/documentLists" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/documentLists";
let options = {
  url: url,
  headers: {
    "Client-Secret": "thisismysecretkey",
    "Content-Type": "application/json",
    "Accept": 'application/json'
  }
};

request(options, function(error, response, body) {
  if (!error && response.statusCode == 200) {
    let info = JSON.parse(body);
    // ...
  } else {
    console.error("Error when calling API! HTTP Code: " + response.statusCode + ", Error message: " + body.errorMessage);
  }
});
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "_id": "64f1daa00c1532914b92",
      "title": "Project files",
      "createdByUser": "571f61330c7f498a2d5812",
      "createDate": "2021-08-24T11:40:16.285Z",
      "modifiedByUser": "571f61330c7f498a2d5812",
      "modifiedDate": "2021-08-24T11:40:16.285Z",
      "archived": false
    }
  ]
}
```

This endpoint retrieves document lists. Use the returned `_id` as `documentListId` when listing or uploading documents in the general document archive.

### HTTP Request

`GET https://app.seventime.se/api/2/documentLists`


## Upload a document

```shell
curl -X POST "https://app.seventime.se/api/2/documents/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"uploadedBy":"571f61330c7f498a2d5812","entityId":"5bae34dca878b5497748","entityType":"200","file":{"fileContent":"base64-encoded-file-content","options":{"fileName":"plan2.pdf","contentType":"application/pdf"}},"folderId":null}'
```

```javascript
let jsonData = {
  uploadedBy: '571f61330c7f498a2d5812',
  entityId: "5bae34dca878b5497748",
  entityType: 200,
  file: {
      fileContent: data,
      options: {
          fileName: 'plan2.pdf',
          contentType: 'application/pdf'
      }
  },
  folderId: null,
};

let options = {
  url: 'https://app.seventime.se/api/2/documents',
  json: jsonData,
  headers: {
    "Client-Secret": "thisismysecretkey",
    "Content-Type": "application/json",
    "Accept": 'application/json'
  }
};

request.post(options, function (error, response, body) {
  if (!error && response.statusCode === 200) {
    console.log('File uploaded');
  } else {
    console.error("ERROR! Unable to upload document: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "success": true,
  "data": {
    "createDate": "2021-08-24T11:40:16.285Z",
    "modifiedDate": "2021-08-24T11:40:16.285Z",
    "_id": "6124daa00c1532914b92",
    "name": "plan2.pdf",
    "path": "https://seventimedev.s3-eu-west-1.amazonaws.com/...",
    "realPath": "1234/workOrders/5bae34dca878b5497748/20210824134016/plan2.pdf",
    "contentType": "application/pdf",
    "size": 20548,
    "user": "571f61330c7f498a2d5812",
    "userName": "Anna Andersson",
    "isLink": false,
    "isFolder": false,
    "folderId": null,
    "isPublic": false
  }
}
```

This endpoint uploads a document or adds a folder. Uploads are supported in two modes:

- Attach to an entity with `entityId` and `entityType`.
- Add to a document list with `documentListId`. Use `folderId` to place the document or folder inside an existing folder in that document list.

To create a folder, send `isFolder: true`. Folder uploads do not require `fileContent` or `contentType`, but `file.options.fileName` is still required due to the current implementation.

### HTTP Request

`POST https://app.seventime.se/api/2/documents/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
uploadedBy         | String   | Yes | Id of the user who uploaded the file
entityId           | String   | Yes* | Id of the parent object, e.g. id of a work order.
entityType         | Number   | Yes* | Entity type of the parent. See table below for available types and corresponding code.
documentListId     | String   | Yes* | Id of the document list. Used instead of `entityId` + `entityType` for the general document archive.
file               | Object   | Yes | Object containing the file and information about the file. See below for more details
folderId           | String   | No | Folder id in which the document will be placed. Defaults to null when omitted.
isFolder           | Boolean  | No | Set to true to create a folder instead of uploading a file.

*Either `entityId` + `entityType` or `documentListId` is required. They cannot be combined. `entityId` + `entityType` are not required for folders when using `documentListId`.

**Available entity types for parent object**

Code | Entity type
--------- | ----------- 
200    | Work order
400    | Invoice
500    | Project
600    | Expense
1100   | Customer
1400   | Quote
1500   | Machine
1600   | Object item
1800   | Supplement order
2300   | Purchase order
2400   | Education log
3100   | Deviation
3200   | Machine log
3300   | Supplier invoice

**What the file object should contain**

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
fileContent         | String   | Yes* | The file content should be included here encoded as base64.
options             | Object   | Yes | Options for the file. This object must contain fileName and contentType. Folder uploads currently still require file.options.fileName due to the current implementation.
fileName            | String   | Yes | Name of the file in Seven Time. This does not need to be the same as the local file
contentType         | String   | Yes* | Content or MIME type of the file.

*Not Required for folders

## Update a document

```shell
curl -X PUT "https://app.seventime.se/api/2/documents/6124daa00c1532914b92?entityId=5bae34dca878b5497748&entityType=200" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"name":"updated-plan.pdf","folderId":null,"isPublic":true}'
```

```javascript
let jsonData = {
  name: 'updated-plan.pdf',
  folderId: null,
  isPublic: true
};

let options = {
  url: 'https://app.seventime.se/api/2/documents/6124daa00c1532914b92?entityId=5bae34dca878b5497748&entityType=200',
  json: jsonData,
  headers: {
    "Client-Secret": "thisismysecretkey",
    "Content-Type": "application/json",
    "Accept": 'application/json'
  }
};

request.put(options, function (error, response, body) {
  if (!error && response.statusCode === 200) {
    console.log('File updated');
  } else {
    console.error("ERROR! Unable to update document: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "success": true,
  "data": {
    "createDate": "2021-08-24T11:40:16.285Z",
    "modifiedDate": "2021-08-25T09:20:40.126Z",
    "_id": "6124daa00c1532914b92",
    "name": "updated-plan.pdf",
    "path": "https://seventimedev.s3-eu-west-1.amazonaws.com/...",
    "realPath": "1234/workOrders/5bae34dca878b5497748/20210824134016/plan2.pdf",
    "contentType": "application/pdf",
    "size": 20548,
    "user": "571f61330c7f498a2d5812",
    "userName": "Anna Andersson",
    "isLink": false,
    "isFolder": false,
    "folderId": null,
    "isPublic": true
  }
}
```

This endpoint updates a document or folder. It can rename the document, move it to another folder, or update the public flag. For documents attached to an entity, include `entityId` and `entityType` as query parameters or in the request body. For documents in a document list, only the document id is required.

### HTTP Request

`PUT https://app.seventime.se/api/2/documents/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the document to update

### Query Parameters

Parameter | Required? | Description
--------- | --------- | -----------
entityId           | Yes* | Id of the parent object for documents attached to an entity.
entityType         | Yes* | Entity type of the parent for documents attached to an entity.

*Required only when the document is attached to an entity. These values can also be sent in the body.

### PUT Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
name               | String   | No | New document or folder name. Cannot be empty.
folderId           | String   | No | Folder id to move the document into. Send `null`, `"null"`, or an empty string to move it to the root. A folder cannot be moved into itself.
isPublic           | Boolean  | No | Public flag for the document.
entityId           | String   | No* | Id of the parent object for documents attached to an entity.
entityType         | Number   | No* | Entity type of the parent for documents attached to an entity.

*Required only when the document is attached to an entity and not sent as query parameters.

## Delete a document

```shell
curl -X DELETE "https://app.seventime.se/api/2/documents/6124daa00c1532914b92?entityId=5bae34dca878b5497748&entityType=200" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json"
```

```javascript
let options = {
  url: 'https://app.seventime.se/api/2/documents/6124daa00c1532914b92?entityId=5bae34dca878b5497748&entityType=200',
  headers: {
    "Client-Secret": "thisismysecretkey",
    "Content-Type": "application/json",
    "Accept": 'application/json'
  }
};

request.delete(options, function (error, response, body) {
  if (!error && response.statusCode === 200) {
    console.log('File deleted');
  } else {
    console.error("ERROR! Unable to delete document: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "success": true
}
```

This endpoint deletes a document or folder. For documents attached to an entity, include `entityId` and `entityType` as query parameters. For documents in a document list, only the document id is required. Deleting a file document also removes the stored file.

### HTTP Request

`DELETE https://app.seventime.se/api/2/documents/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the document to delete

### Query Parameters

Parameter | Required? | Description
--------- | --------- | -----------
entityId           | Yes* | Id of the parent object for documents attached to an entity.
entityType         | Yes* | Entity type of the parent for documents attached to an entity.

*Required only when the document is attached to an entity.
