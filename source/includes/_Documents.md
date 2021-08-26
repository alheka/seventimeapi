# Documents
## Get Documents

Documents are included when fetching other objects, e.g. work orders or projects. They are found in an array named documents. The objects in the array contain a path which can be used to download the documents. Folders are also included and will have the flag isFolder as true.

> Fetching a work order returns a documents array like this:

```json
{
  "data": {
    //...
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
        "isPublic": false,
      },
    ],
    //..
  }
}
```



## Upload a document

```shell
curl -X POST "https://app.seventime.se/api/2/documents/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"uploadedBy":"571f61330c7f498a2d5812","entityId":"5bae34dca878b5497748","entityType":"200","file":"{fileContent: data, options: {fileName: plan2.pdf, contentType: application/pdf}}","folderId":"null"}'
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
  success: true
}
```

This endpoint uploads a document or adds a folder.

### HTTP Request

`POST https://app.seventime.se/api/2/documents/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
uploadedBy         | String   | Yes | Id of the user who uploaded the file
entityId           | String   | Yes* | Id of the parent object, e.g. id of a work order. 
entityType         | Number   | Yes* | Entity type of the parent. See table below for available types and corresponding code.
file               | Object   | Yes | Object containing the file and information about the file. See below for more details
folderId           | String   | Yes | Folder id in which the document will be placed in

*Not Required for folders

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
options             | Object   | Yes | Options for the file. This object should contain fileName and contentType
fileName            | String   | Yes | Name of the file in Seven Time. This does not need to be the same as the local file
contentType         | String   | Yes* | Content or MIME type of the file.

*Not Required for folders
