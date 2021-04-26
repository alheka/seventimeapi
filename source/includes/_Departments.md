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
      "_id": "59d05abdc471b72e4901079",
      "name": "Utveckling",
      "departmentNumber": "2",
      "isActive": true,
      "managerIds": [],
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

E.g. `https://app.seventime.se/api/2/departments/?`

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get a specific Department

```shell
curl "https://app.seventime.se/api/2/departments/59d05abdc471b72e4901079" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/departments/59d05abdc471b72e4901079";
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
    "_id": "59d05abdc471b72e4901079",
    "name": "Utveckling",
    "departmentNumber": "2",
    "isActive": true,
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
