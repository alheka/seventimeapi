# Vehicles
## Get Vehicles

```shell
curl "https://app.seventime.se/api/2/vehicles/?limit=5&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/vehicles/?limit=5&page=1";
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
    "totalResources": 28,
    "totalPages": 6,
    "currentPage": 2
  },
  "data": [
    {
      "_id": "55782f0382da2f8544689751",
      "name": "Audi Q8",
      "registrationNumber": "ABC123",
      "isActive": true,
      "createDate": "2016-06-08T14:45:42.546Z",
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves vehicles.

### HTTP Request

`GET https://app.seventime.se/api/2/vehicles`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy                      |  | If specified, a sort will be made on the specified parameter
sortDirection               |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


## Get a specific Vehicles

```shell
curl "https://app.seventime.se/api/2/vehicles/55782f0382da2f8544689751" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/vehicles/55782f0382da2f8544689751";
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
    "_id": "55782f0382da2f8544689751",
    "name": "Audi Q8",
    "registrationNumber": "ABC123",
    "isActive": true,
    "createDate": "2016-06-07T13:20:04.346Z",
  }
}
```

This endpoint retrieves a specific vehicle.


### HTTP Request

`GET https://app.seventime.se/api/2/vehicle/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the vehicle to retrieve
