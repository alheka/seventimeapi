# Price Lists

## Get price lists

```shell
curl "https://app.seventime.se/api/2/priceLists/?limit=10&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/priceLists/?limit=10&page=1";
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
    "totalResources": 5,
    "totalPages": 1,
    "currentPage": 1
  },
  "data": [
    {
      "_id": "58c1504a658fb5911d6489528",
      "name": "Grosslistan",
      "isActive": true
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves price lists.

### HTTP Request

`GET https://app.seventime.se/api/2/priceLists`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


## Get a specific Price List

```shell
curl "https://app.seventime.se/api/2/priceLists/58c1504a658fb5911d6489528" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/priceLists/58c1504a658fb5911d6489528";
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
    "_id": "58c1504a658fb5911d6489528",
    "isActive": true,
    "name": "ÅF-prislista"
  }
}
```

This endpoint retrieves a specific price list.


### HTTP Request

`GET https://app.seventime.se/api/2/priceLists/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the price list to retrieve
