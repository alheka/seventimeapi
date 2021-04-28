# Result Units
## Get Result Units

```shell
curl "https://app.seventime.se/api/2/resultUnits" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/resultUnits";
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
      "_id": "57076abe8010bd225413654",
      "name": "Kontor Syd",
      "code": "Syd",
      "isActive": true,
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves purchase orders.

### HTTP Request

`GET https://app.seventime.se/api/2/resultUnits`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy                              |  | If specified, a sort will be made on the specified parameter
sortDirection                       |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get a specific Result Unit

```shell
curl "https://app.seventime.se/api/2/resultUnits/57076abe8010bd225413654" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/resultUnits/57076abe8010bd225413654";
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
    "_id": "57076abe8010bd225413654",
    "name": "Kontor Syd",
    "code": "Syd",
    "isActive": true,
  }
}
```

This endpoint retrieves a specific result unit.


### HTTP Request

`GET https://app.seventime.se/api/2/resultUnits/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the result unit to retrieve
