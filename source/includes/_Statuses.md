# Statuses

## Get Statuses

```shell
curl "https://app.seventime.se/api/2/statuses/?entityType=200" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/statuses/?entityType=200";
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
[
  {
    "_id": "582f7cabd16fdb974185235",
    "statusName": "Ej planerad",
    "color": "FF5722",
    "plannedStatus": false,
    "inProgressStatus": false,
    "closedStatus": false,
    "isActive": true
  },
  {
    // ...
  }
]
```

This endpoint retrieves the statuses configured for an entity type. Note that the response is a plain JSON array and is not wrapped in a `data` property.

### HTTP Request

`GET https://app.seventime.se/api/2/statuses/`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
entityType    |  | **Required.** Number corresponding to the entity type to retrieve statuses for, e.g. 200 for work orders or 500 for projects. If omitted, HTTP 400 is returned with the `errorMessage` "Entity type required".

The statuses are returned in the order they are configured. Sorting parameters are not supported.
