# Object Items

Object items (objects) are e.g. buildings, apartments, facilities or installations. They are organized in a tree: an object item can have a `parent` object item and children of its own.

The tree is described by these fields:

Field | Description
--------- | -----------
parent       | Id of the parent object item. `null` for object items on the top level
path         | Ids of the object item and its ancestors, from the top level, separated by `#`
readablePath | Names of the object item and its ancestors, from the top level, separated by `#`
hasChildren  | `true` if the object item has children

Documents on object items are handled with the [Documents API](#documents), using entity type `1600`. The [webhook events](#available-events) `objectitem.created`, `objectitem.updated`, `objectitem.document.created` and `objectitem.document.updated` tell when object items and their documents are created or changed.

## Get Object Items

```shell
curl "https://app.seventime.se/api/2/objectItems/?limit=10&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/objectItems/?limit=10&page=1";
let options = {
  url: url,
  headers: {
    "Client-Secret": "thisismysecretkey"
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
  "meta": {
    "totalResources": 30,
    "totalPages": 3,
    "currentPage": 1,
    "hasMore": true
  },
  "data": [
    {
      "_id": "6512a0c4e5b8a43c2f9d1a77",
      "objectItemNumber": "1042",
      "objectItemType": "6512a01fe5b8a43c2f9d1a10",
      "objectItemTypeName": "Building",
      "name": "Building A",
      "address": "Östra Gatan 129",
      "address2": "",
      "zipCode": "123 45",
      "city": "Stockholm",
      "country": "",
      "locationCoordinates": [18.0686, 59.3293],
      "locationIsUserSpecified": false,
      "phone": "",
      "email": "",
      "customer": "571f61330c7f498a4712448b",
      "customerName": "Anna Andersson",
      "customerNumber": "733352",
      "contactPerson": null,
      "contactPersonName": "",
      "notes": "",
      "purchaseDate": null,
      "distributor": null,
      "distributorName": "",
      "customFields": [],
      "isActive": true,
      "parent": "6512a09be5b8a43c2f9d1a55",
      "path": "6512a09be5b8a43c2f9d1a55#6512a0c4e5b8a43c2f9d1a77",
      "readablePath": "Area North#Building A",
      "hasChildren": true,
      "createdDate": "2024-01-15T08:00:00.000Z",
      "createdByUser": "5113986056b831a917962158",
      "createdByUserName": "Anna Andersson",
      "modifiedDate": "2024-02-01T10:00:00.000Z",
      "modifiedByUser": "5113986056b831a917962158",
      "modifiedByUserName": "Anna Andersson"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves object items. Documents are not included in the list, use [Get a specific Object Item](#get-a-specific-object-item) or the [Documents API](#documents) to get them.

### HTTP Request

`GET https://app.seventime.se/api/2/objectItems`

### Query Parameters

E.g. `https://app.seventime.se/api/2/objectItems/?parent=null`

Parameter | Default | Description
--------- | ------- | -----------
name               |  | If specified, object items that match the parameter will be included.
objectItemNumber   |  | If specified, object items that match the parameter will be included.
objectItemType     |  | Id of an object item type. If specified, object items of that type will be included.
objectItemTypeName |  | If specified, object items that match the parameter will be included.
city               |  | If specified, object items that match the parameter will be included.
customer           |  | Id of a customer. If specified, object items connected to the customer will be included.
parent             |  | Id of an object item. If specified, the children of that object item will be included. Use `null` to get the object items on the top level.
isActive           |  | "true" or "false". If specified, active or archived object items will be included.
lastModified       |  | If specified, object items that have been modified since the specified timestamp will be included. Accepted formats: 'YYYY-MM-DD', 'YYYY-MM-DD HH:MM', 'YYYY-MM-DD HH:MM:SS', 'YYYY-MM-DDTHH:MM', 'YYYY-MM-DDTHH:MM:SS'
sortBy             | name | If specified, a sort will be made on the specified parameter
sortDirection      | ascending | "ascending" or "descending". The sort order will be ascending or descending
limit              | 100 | Number of object items per page. Maximum 500
page               | 1 | Page number

## Get a specific Object Item

```shell
curl "https://app.seventime.se/api/2/objectItems/6512a0c4e5b8a43c2f9d1a77" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/objectItems/6512a0c4e5b8a43c2f9d1a77";
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
    "_id": "6512a0c4e5b8a43c2f9d1a77",
    "objectItemNumber": "1042",
    "objectItemType": "6512a01fe5b8a43c2f9d1a10",
    "objectItemTypeName": "Building",
    "name": "Building A",
    "address": "Östra Gatan 129",
    "zipCode": "123 45",
    "city": "Stockholm",
    "customer": "571f61330c7f498a4712448b",
    "customerName": "Anna Andersson",
    "customerNumber": "733352",
    "isActive": true,
    "parent": "6512a09be5b8a43c2f9d1a55",
    "path": "6512a09be5b8a43c2f9d1a55#6512a0c4e5b8a43c2f9d1a77",
    "readablePath": "Area North#Building A",
    "hasChildren": true,
    "customFields": [
      {
        "_id": "6512a0c4e5b8a43c2f9d1a78",
        "fieldId": "6512a011e5b8a43c2f9d1a01",
        "value": "3"
      }
    ],
    "documents": [
      {
        "_id": "6124daa00c1532914b92",
        "name": "plan1.pdf",
        "path": "https://seventimedev.s3-eu-west-1.amazonaws.com/...",
        "realPath": "1234/objectItems/6512a0c4e5b8a43c2f9d1a77/plan1_20240115090000.pdf",
        "contentType": "application/pdf",
        "size": 20548,
        "user": "5113986056b831a917962158",
        "userName": "Anna Andersson",
        "isLink": false,
        "isFolder": false,
        "folderId": null,
        "isPublic": false,
        "createDate": "2024-01-15T09:00:00.000Z",
        "modifiedDate": "2024-01-15T09:00:00.000Z"
      }
    ],
    "createdDate": "2024-01-15T08:00:00.000Z",
    "createdByUser": "5113986056b831a917962158",
    "createdByUserName": "Anna Andersson",
    "modifiedDate": "2024-02-01T10:00:00.000Z"
    // ...
  }
}
```

This endpoint retrieves a specific object item, including its documents and folders. The `path` of a document is a download URL that is valid for one hour.

### HTTP Request

`GET https://app.seventime.se/api/2/objectItems/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the object item to retrieve

## Get Object Item Types

```shell
curl "https://app.seventime.se/api/2/objectItemTypes" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/objectItemTypes";
let options = {
  url: url,
  headers: {
    "Client-Secret": "thisismysecretkey"
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
      "_id": "6512a01fe5b8a43c2f9d1a10",
      "name": "Building",
      "isActive": true,
      "iconClass": "icon-building"
    },
    {
      "_id": "6512a01fe5b8a43c2f9d1a11",
      "name": "Apartment",
      "isActive": true,
      "iconClass": "icon-home"
    }
  ]
}
```

This endpoint retrieves all object item types.

### HTTP Request

`GET https://app.seventime.se/api/2/objectItemTypes`

## Create an Object Item

```shell
curl -X POST "https://app.seventime.se/api/2/objectItems/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"createdByUser":"5113986056b831a917962158","name":"Building A","parent":"6512a09be5b8a43c2f9d1a55","objectItemType":"6512a01fe5b8a43c2f9d1a10","address":"Östra Gatan 129","zipCode":"123 45","city":"Stockholm","customer":"571f61330c7f498a4712448b"}'
```

```javascript
let jsonData = {
  createdByUser: '5113986056b831a917962158',
  name: 'Building A',
  parent: '6512a09be5b8a43c2f9d1a55',
  objectItemType: '6512a01fe5b8a43c2f9d1a10',
  address: 'Östra Gatan 129',
  zipCode: '123 45',
  city: 'Stockholm',
  customer: '571f61330c7f498a4712448b'
};

let options = {
  url: 'https://app.seventime.se/api/2/objectItems',
  json: jsonData,
  headers: {
    "Client-Secret": "thisismysecretkey",
    "Content-Type": "application/json",
    "Accept": 'application/json'
  }
};

request.post(options, function (error, response, body) {
  if (!error && response.statusCode === 200) {
    console.log(body);
  } else {
    console.error("ERROR! Unable to create object item: " + error);
    console.error(body);
  }
});
```

> The above command returns the created object item, structured like this:

```json
{
  "_id": "6512a0c4e5b8a43c2f9d1a77",
  "objectItemNumber": "1042",
  "objectItemType": "6512a01fe5b8a43c2f9d1a10",
  "objectItemTypeName": "Building",
  "name": "Building A",
  "address": "Östra Gatan 129",
  "zipCode": "123 45",
  "city": "Stockholm",
  "locationCoordinates": [18.0686, 59.3293],
  "customer": "571f61330c7f498a4712448b",
  "customerName": "Anna Andersson",
  "customerNumber": "733352",
  "isActive": true,
  "parent": "6512a09be5b8a43c2f9d1a55",
  "path": "6512a09be5b8a43c2f9d1a55#6512a0c4e5b8a43c2f9d1a77",
  "readablePath": "Area North#Building A",
  "customFields": [],
  "documents": [],
  "createdDate": "2024-01-15T08:00:00.000Z",
  "createdByUser": "5113986056b831a917962158",
  "createdByUserName": "Anna Andersson",
  "modifiedDate": "2024-01-15T08:00:00.000Z"
  // ...
}
```

This endpoint creates an object item. If the address is specified and `locationCoordinates` is not, the position on the map is looked up from the address.

### HTTP Request

`POST https://app.seventime.se/api/2/objectItems/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
createdByUser       | String  | Yes | Id of the user who created the object item
name                | String  | Yes | Name of the object item
objectItemNumber    | String  | No | Object number. Ignored when automatic object numbering is turned on in the object settings, the next number is then used.
parent              | String  | No | Id of the parent object item. Not specified or `null` creates the object item on the top level
objectItemType      | String  | No | Id of the object item type. See [Get Object Item Types](#get-object-item-types)
customer            | String  | No | Id of the customer
contactPerson       | String  | No | Id of a contact person. The contact person must belong to the customer of the object item
distributor         | String  | No | Id of the distributor
address             | String  | No | Address
address2            | String  | No | Address 2
zipCode             | String  | No | Zip code
city                | String  | No | City
country             | String  | No | Country
phone               | String  | No | Phone
email               | String  | No | Email
notes               | String  | No | Notes
purchaseDate        | String  | No | Purchase date, 'YYYY-MM-DD'
locationCoordinates | Array   | No | Position on the map, `[longitude, latitude]`. When specified, the position is not looked up from the address
customFields        | Array   | No | Custom field values, `[{"fieldId": "...", "value": "..."}]`. `fieldId` is the `_id` of a custom field for entity type `1600`, see [Custom Fields](#custom-fields)
isActive            | Boolean | No | `false` creates an archived object item. Default `true`

The names (`customerName`, `objectItemTypeName` etc.) are set from the ids and cannot be set directly.

## Update an Object Item

```shell
curl -X PUT "https://app.seventime.se/api/2/objectItems/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"6512a0c4e5b8a43c2f9d1a77","modifiedByUser":"5113986056b831a917962158","name":"Building B","notes":"Key in the box by the door"}'
```

```javascript
let jsonData = {
  _id: '6512a0c4e5b8a43c2f9d1a77',
  modifiedByUser: '5113986056b831a917962158',
  name: 'Building B',
  notes: 'Key in the box by the door'
};

let options = {
  url: 'https://app.seventime.se/api/2/objectItems',
  json: jsonData,
  headers: {
    "Client-Secret": "thisismysecretkey",
    "Content-Type": "application/json",
    "Accept": 'application/json'
  }
};

request.put(options, function (error, response, body) {
  if (!error && response.statusCode === 200) {
    console.log(body);
  } else {
    console.error("ERROR! Unable to update object item: " + error);
    console.error(body);
  }
});
```

> The above command returns the updated object item, structured like [Create an Object Item](#create-an-object-item).

This endpoint updates an object item. Only the specified fields are changed. Use `null` or `""` to clear `customer`, `contactPerson`, `objectItemType`, `distributor`, `purchaseDate` and `locationCoordinates`.

- Changing `parent` moves the object item, including its children, in the tree. `null` moves it to the top level. An object item cannot be moved below itself.
- When `customer` is changed and `contactPerson` is not specified, the contact person is removed.
- `customFields` only changes the specified custom fields, the other values are kept.
- `isActive: false` archives the object item and `isActive: true` restores it.
- Setting `locationCoordinates` to `null` makes the position be looked up from the address again.

Object items cannot be deleted with the API.

### HTTP Request

`PUT https://app.seventime.se/api/2/objectItems/`

### PUT Parameters

All POST parameters except `createdByUser`, plus:

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id            | String | Yes | Id of the object item to update
modifiedByUser | String | Yes | Id of the user who updated the object item

### Permissions

With an API key connected to a user, the user's permissions for objects are used: viewing objects for the GET endpoints and editing objects for POST and PUT. Moving an object item (changing `parent`) also requires the permission to move objects.
