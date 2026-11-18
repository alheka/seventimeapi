# Departments

## Get Departments


```shell
curl "https://app.seventime.se/api/2/departments" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/departments";
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
  "meta": {
    "totalResources": 3,
    "totalPages": 1,
    "currentPage": 1
  },
  "data": [
    {
      "_id": "59d05abda1b2c3d4e5001015",
      "createdAt": "2017-10-01T03:02:21.120Z",
      "updatedAt": "2017-10-02T05:19:24.214Z",
      "name": "Utveckling",
      "departmentNumber": "2",
      "isActive": true,
      "managerIds": []
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves departments.

### HTTP Request

`GET https://app.seventime.se/api/2/departments`

### Query Parameters

E.g. `https://app.seventime.se/api/2/departments/?sortBy=departmentNumber&sortDirection=descending`

Parameter | Default | Description
--------- | ------- | -----------
lastModified |  | If specified, departments that have been modified since the specified timestamp will be included (compared with `updatedAt`). Accepted formats: 'YYYY-MM-DD', 'YYYY-MM-DD HH:MM', 'YYYY-MM-DD HH:MM:SS', 'YYYY-MM-DDTHH:MM', 'YYYY-MM-DDTHH:MM:SS'. An invalid value returns HTTP 400
cursor       |  | `first` to page with a cursor instead of `page`, then `meta.nextCursor` from the previous response. Can't be combined with `page`, `sortBy` or `sortDirection`. See [Paging with a cursor](#paging-with-a-cursor)
sortBy | name | If specified, a sort will be made on the specified parameter
sortDirection | ascending | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending
limit | 100 | Number of departments per page. Maximum 500
page | 1 | Page number

## Get a specific Department

```shell
curl "https://app.seventime.se/api/2/departments/59d05abda1b2c3d4e5001015" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/departments/59d05abda1b2c3d4e5001015";
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
    "managerIds": [],
    "_id": "59d05abda1b2c3d4e5001015",
    "createdAt": "2017-10-01T03:02:21.120Z",
    "updatedAt": "2017-10-02T05:19:24.214Z",
    "name": "Utveckling",
    "departmentNumber": "2",
    "isActive": true
  }
}
```

This endpoint retrieves a specific department.



### HTTP Request

`GET https://app.seventime.se/api/2/departments/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the department to retrieve
