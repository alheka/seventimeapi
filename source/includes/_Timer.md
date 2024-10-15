# Timers
## Get Active Timers


```shell
curl "https://app.seventime.se/api/2/timers/?limit=3&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/timers/?limit=3&page=1";
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
    "totalResources": 2,
    "totalPages": 1,
    "currentPage": 1
  },
  "data": [
    {
      "startLocation": {
        "type": "Point",
        "coordinates": []
      },
      "_id": "670813733j31273j321j2",
      "startTimestamp": "2024-10-15T14:21:02.720Z",
      "realStartTimestamp": "2024-10-15T14:21:02.720Z",
      "machineTimeSupplements": [],
      "machineTimePrices": [],
      "user": "51718241fdb7084835249227"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves all active timers.

### HTTP Request

`GET https://app.seventime.se/api/2/timers`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
user               |  | If specified, timers that match the parameter will be included.
customer           |  | If specified, timers that match the parameter will be included.
project            |  | If specified, timers that match the parameter will be included.
task               |  | If specified, timers that match the parameter will be included.
timeCategory       |  | If specified, timers that match the parameter will be included.
workOrder          |  | If specified, timers that match the parameter will be included.
sortBy             |  | If specified, a sort will be made on the specified parameter
sortDirection      |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


## Start a timer

```shell
curl -X POST "https://app.seventime.se/api/2/startTimer/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"user":"51718241fdb7084835249227"}'
```

```javascript
let jsonData = {
  user: '51203146506d961c03036589741',
};

let options = {
  url: 'https://app.seventime.se/api/2/startTimer',
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
    console.error("ERROR! Unable to start timer: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "startLocation": {
    "type": "Point",
    "coordinates": []
  },
  "_id": "670813733j31273j321j2",
  "startTimestamp": "2024-10-15T14:21:02.720Z",
  "realStartTimestamp": "2024-10-15T14:21:02.720Z",
  "machineTimeSupplements": [],
  "machineTimePrices": [],
  "user": "51718241fdb7084835249227"
}
```

This endpoint starts a timer

### HTTP Request

`POST https://app.seventime.se/api/2/timers/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
user                | String | Yes | Id of the user on the timer
customer            | String | No  | Id of the customer
project             | String | No  | Id of the project
workOrder           | String | No  | Id of the work order
timeCategory        | String | No  | Id of the time category
task                | String | No  | Id of the task

## Stop a Timer

```shell
curl -X POST "https://app.seventime.se/api/2/stopTimer/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"user":"51718241fdb7084835249227"}'
```

```javascript
let jsonData = {
  user: '51718241fdb7084835249227'
};

let options = {
  url: 'https://app.seventime.se/api/2/stopTimer',
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
    console.log("Timer stopped and time log created: _id: " + body._id);
  } else {
    console.error("ERROR! Unable to stop timer: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "startLocation": { type: 'Point', coordinates: [] },
  "stopLocation": { type: 'Point', coordinates: [] },
  "allDay": false,
  "status": 1,
  "isInvoiceable": true,
  "isInvoiced": false,
  "_id": "5fbcfe75ba9312280e2145897521",
  "timestamp": "2020-11-19T12:00:00.000Z",
  "realTimestamp": "2020-11-19T12:00:00.000Z",
  "createDate": "2020-11-24T12:37:09.258Z",
  "unSocialHoursCosts": [],
  "customFields": [],
  "machineTimePrices": [],
  "machineTimeSupplements": [],
  "user": "51203146506d961c03036589741",
  "userName": "Anna Andersson",
  "endTimestamp": "2020-11-19T17:00:00.000Z",
  "realEndTimestamp": "2020-11-19T17:00:00.000Z",
  "time": 5,
  "invoiceableTime": 5,
  "pricePerHour": 777,
  "price": 777
}
"Timer stopped and time log created: _id: 51203146506d961c35798485"
```

This endpoint stops a timer and returns the created time log

### HTTP Request

`POST https://app.seventime.se/api/2/stopTimer/`

### DELETE Parameters

Parameter | Type | Required? | Description
--------- | ----------- |-----------| -----------
_id             | String | Yes*      | Id of the timer (*required if user is not specified)
user            | String | Yes*      | Id of the user on the timer (*required if _id is not specified)
