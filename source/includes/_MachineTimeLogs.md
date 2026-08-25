# Machine Time Logs

## Get Machine Time Logs

```shell
curl "https://app.seventime.se/api/2/machineTimeLogs/?limit=20&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/machineTimeLogs/?limit=20&page=1";
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
    "totalResources": 55,
    "totalPages": 28,
    "currentPage": 27
  },
  "data": [
    {
      "_id": "59ef428433092a453647952813",
      "time": 12,
      "invoiceableTime": 12,
      "description": "12",
      "internalDescription": "",
      "attestedBy": null,
      "invoice": null,
      "machine": "59e75917ae561db737946137",
      "machineName": "Grävare",
      "user": "51203146506d966481937",
      "userName": "Anna Andersson",
      "department": "58b30abde244b75d15648293",
      "departmentName": "Utveckling",
      "customer": null,
      "customerName": null,
      "project": null,
      "projectName": null,
      "workOrder": null,
      "workOrderTitle": "",
      "workOrderNumber": 0,
      "pricePerHour": 0,
      "price": 0,
      "cost": 0,
      "createDate": "2017-10-24T13:39:16.764Z",
      "isInvoiced": false,
      "isInvoiceable": true,
      "status": 1,
      "timestamp": "2017-10-24T13:39:06.144Z"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves machine time logs.

### HTTP Request

`GET https://app.seventime.se/api/2/machineTimeLogs`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
fromDate         |  | If specified, machine time logs registered after or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
toDate           |  | If specified, machine time logs registered before or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
sortBy           |  | If specified, a sort will be made on the specified parameter
sortDirection    |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


## Get a specific Machine Time Log

```shell
curl "https://app.seventime.se/api/2/machineTimeLogs/5a4bc02e40a13d77915827619" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/machineTimeLogs/5a4bc02e40a13d77915827619";
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
    "status": 1,
    "isInvoiceable": true,
    "isInvoiced": false,
    "_id": "5a4bc02e40a13d77915827619",
    "time": 12,
    "invoiceableTime": 12,
    "description": "12",
    "internalDescription": "",
    "attestedBy": null,
    "invoice": null,
    "machine": "59e75917ae561db7364829167",
    "machineName": "Grävare",
    "user": "51203146506d97461389557821",
    "userName": "Anna Andersson",
    "department": "58b30abde244b75d464826137958",
    "departmentName": "Utveckling",
    "customer": null,
    "customerName": null,
    "project": null,
    "projectName": null,
    "workOrder": null,
    "workOrderTitle": "",
    "workOrderNumber": 0,
    "pricePerHour": 0,
    "price": 0,
    "cost": 0,
    "createDate": "2017-10-24T13:39:16.764Z",
    "timestamp": "2017-10-24T13:39:06.144Z"
  }
}
```

This endpoint retrieves a specific machine time log.



### HTTP Request

`GET https://app.seventime.se/api/2/machineTimeLogs/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the machine time log to retrieve

## Create a Machine Time Log

```shell
curl -X POST "https://app.seventime.se/api/2/machineTimeLogs/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"user":"51203146506d97461389557821","machine":"59e75917ae561db7364829167","time":2,"timestamp":"2024-01-15T08:00:00.000Z"}'
```

```javascript
let jsonData = {
  user: '51203146506d97461389557821',
  machine: '59e75917ae561db7364829167',
  time: 2,
  timestamp: '2024-01-15T08:00:00.000Z'
};

let options = {
  url: 'https://app.seventime.se/api/2/machineTimeLogs',
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
    console.error("ERROR! Unable to create machine time log: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json
{
  "_id": "65a50f80d1e44854f9c12345",
  "time": 2,
  "machine": "59e75917ae561db7364829167",
  "user": "51203146506d97461389557821",
  "timestamp": "2024-01-15T08:00:00.000Z"
}
```

This endpoint creates a machine time log.

### HTTP Request

`POST https://app.seventime.se/api/2/machineTimeLogs/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
user                | String | Yes | Id of the user registering the machine time log
machine             | String | Yes | Id of the machine
otherUser           | String | No  | Id of another user, if the log should be registered for another user
customer            | String | No  | Id of the customer
project             | String | No  | Id of the project
workOrder           | String | No  | Id of the work order
time                | Number | Yes | Registered time in hours
description         | String | No  | Description
internalDescription | String | No  | Internal description
invoiceableTime     | Number | No  | Invoiceable time in hours
isInvoiceable       | Boolean | No | If the machine time log is invoiceable
timestamp           | String | Yes | Time log date and time in ISO 8601 format
status              | Number | No  | Status of the machine time log

## Update a Machine Time Log

```shell
curl -X PUT "https://app.seventime.se/api/2/machineTimeLogs/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"65a50f80d1e44854f9c12345","user":"51203146506d97461389557821","machine":"59e75917ae561db7364829167","time":3,"timestamp":"2024-01-15T08:00:00.000Z"}'
```

```javascript
let jsonData = {
  _id: '65a50f80d1e44854f9c12345',
  user: '51203146506d97461389557821',
  machine: '59e75917ae561db7364829167',
  time: 3,
  timestamp: '2024-01-15T08:00:00.000Z'
};

let options = {
  url: 'https://app.seventime.se/api/2/machineTimeLogs',
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
    console.error("ERROR! Unable to update machine time log: " + error);
    console.error(body);
  }
});
```

This endpoint updates a machine time log.

### HTTP Request

`PUT https://app.seventime.se/api/2/machineTimeLogs/`

### PUT Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                 | String | Yes | Id of the machine time log
user                | String | Yes | Id of the user registering the machine time log
machine             | String | Yes | Id of the machine
otherUser           | String | No  | Id of another user, if the log should be registered for another user
customer            | String | No  | Id of the customer
project             | String | No  | Id of the project
workOrder           | String | No  | Id of the work order
time                | Number | Yes | Registered time in hours
description         | String | No  | Description
internalDescription | String | No  | Internal description
invoiceableTime     | Number | No  | Invoiceable time in hours
isInvoiceable       | Boolean | No | If the machine time log is invoiceable
timestamp           | String | Yes | Time log date and time in ISO 8601 format
status              | Number | No  | Status of the machine time log

## Delete a Machine Time Log

```shell
curl -X DELETE "https://app.seventime.se/api/2/machineTimeLogs/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"65a50f80d1e44854f9c12345","deletedByUser":"51203146506d97461389557821"}'
```

```javascript
let jsonData = {
  _id: '65a50f80d1e44854f9c12345',
  deletedByUser: '51203146506d97461389557821'
};

let options = {
  url: 'https://app.seventime.se/api/2/machineTimeLogs',
  json: jsonData,
  headers: {
    "Client-Secret": "thisismysecretkey",
    "Content-Type": "application/json",
    "Accept": 'application/json'
  }
};

request.delete(options, function (error, response, body) {
  if (!error && response.statusCode === 200) {
    console.log(body);
  } else {
    console.error("ERROR! Unable to delete machine time log: " + error);
    console.error(body);
  }
});
```

This endpoint deletes a machine time log.

### HTTP Request

`DELETE https://app.seventime.se/api/2/machineTimeLogs/`

### DELETE Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id             | String | Yes | Id of the machine time log
deletedByUser   | String | Yes | Id of the user who deleted the machine time log
