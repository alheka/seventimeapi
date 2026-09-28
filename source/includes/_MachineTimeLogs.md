# Machine Time Logs

## Get Machine Time Logs

```shell
curl "https://app.seventime.se/api/2/machineTimeLogs/?fromDate=2017-10-01&toDate=2017-10-31&limit=20&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/machineTimeLogs/?fromDate=2017-10-01&toDate=2017-10-31&limit=20&page=1";
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
    "totalResourcesIsExact": true,
    "totalPages": 3,
    "currentPage": 1,
    "hasMore": true,
    "nextPage": 2
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

At least one filter, e.g. a date range or a user, has to be specified. A request without any filter returns HTTP status 422 with the code `QUERY_TOO_BROAD`.

The result is paginated. `meta.totalResources` is capped at 2000; if there are more matching machine time logs, `meta.totalResourcesIsExact` is false and `meta.totalPages` is null. Use `meta.hasMore` and `meta.nextPage` to fetch the next page.

### HTTP Request

`GET https://app.seventime.se/api/2/machineTimeLogs`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
fromDate         |  | If specified, machine time logs registered after or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
toDate           |  | If specified, machine time logs registered before or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
user             |  | If specified, machine time logs registered for the user with this id will be included
machineName      |  | If specified, machine time logs for the machine with this name will be included
customerName     |  | If specified, machine time logs for the customer with this name will be included
projectName      |  | If specified, machine time logs for the project with this name will be included
workOrderTitle   |  | If specified, machine time logs for the work order with this title will be included
workOrderNumber  |  | If specified, machine time logs for the work order with this number will be included
departmentName   |  | If specified, machine time logs for the department with this name will be included
limit            | 100 | Number of machine time logs per page. Maximum 500
page             | 1 | Page number
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
  -d '{"createdByUser":"51203146506d97461389557821","user":"51203146506d97461389557821","machine":"59e75917ae561db7364829167","time":2,"timestamp":"2024-01-15T08:00:00.000Z","description":"Excavation"}'
```

```javascript
let jsonData = {
  createdByUser: '51203146506d97461389557821',
  user: '51203146506d97461389557821',
  machine: '59e75917ae561db7364829167',
  time: 2,
  timestamp: '2024-01-15T08:00:00.000Z',
  description: 'Excavation'
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

> The above command returns the created machine time log, structured like this:

```json
{
  "_id": "65a50f80d1e44854f9c12345",
  "time": 2,
  "description": "Excavation",
  "internalDescription": "",
  "machine": "59e75917ae561db7364829167",
  "machineName": "Grävare",
  "user": "51203146506d97461389557821",
  "userName": "Anna Andersson",
  "pricePerHour": 850,
  "price": 1700,
  "cost": 0,
  "isInvoiced": false,
  "isInvoiceable": true,
  "timestamp": "2024-01-15T08:00:00.000Z"
}
```

This endpoint creates a machine time log.

The price of a machine time log is always calculated from the price per hour of the machine. The fields `price` and `pricePerHour` cannot be set via the API; sending either of them results in an error.

The time can be given either with `time`, or with `timestamp` and `endTimestamp`, in which case the time is calculated from the difference between them. If `timestamp` is omitted the current date and time is used.

### HTTP Request

`POST https://app.seventime.se/api/2/machineTimeLogs/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
createdByUser       | String | Yes | Id of the user creating the machine time log
machine             | String | Yes | Id of the machine
user                | String | No  | Id of the user the machine time log is registered for
time                | Number | Yes* | Registered time in hours. Must be a positive number
timestamp           | String | No  | Start date and time in ISO 8601 format. Defaults to the current date and time
endTimestamp        | String | No* | End date and time in ISO 8601 format. Cannot be before `timestamp`
customer            | String | No  | Id of the customer
project             | String | No  | Id of the project
workOrder           | String | No  | Id of the work order
department          | String | No  | Id of the department
resultUnit          | String | No  | Id of the result unit
costAccount         | String | No  | Id of the cost account
description         | String | No  | Description
internalDescription | String | No  | Internal description
isInvoiceable       | Boolean | No | If the machine time log is invoiceable
supplementOrder     | Boolean | No | If the machine time log is a supplement order
supplementOrderTime | Number | No  | Supplement order time in hours. Only used when `supplementOrder` is true

*`time` is required unless `endTimestamp` is given.

<aside class="warning">
The fields <code>price</code> and <code>pricePerHour</code> cannot be set. The price is calculated from the machine's price per hour.
</aside>

## Update a Machine Time Log

```shell
curl -X PUT "https://app.seventime.se/api/2/machineTimeLogs/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"65a50f80d1e44854f9c12345","modifiedByUser":"51203146506d97461389557821","time":3}'
```

```javascript
let jsonData = {
  _id: '65a50f80d1e44854f9c12345',
  modifiedByUser: '51203146506d97461389557821',
  time: 3
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

> The above command returns the updated machine time log, structured like this:

```json
{
  "_id": "65a50f80d1e44854f9c12345",
  "time": 3,
  "description": "Excavation",
  "internalDescription": "",
  "machine": "59e75917ae561db7364829167",
  "machineName": "Grävare",
  "user": "51203146506d97461389557821",
  "userName": "Anna Andersson",
  "pricePerHour": 850,
  "price": 2550,
  "cost": 0,
  "isInvoiced": false,
  "isInvoiceable": true,
  "timestamp": "2024-01-15T08:00:00.000Z",
  "modifiedDate": "2024-01-16T10:12:00.000Z"
}
```

This endpoint updates a machine time log. Only the fields included in the request are updated. The price is recalculated from the machine's price per hour.

A machine time log that has been invoiced cannot be updated. The fields `isInvoiced`, `invoicedDate` and `invoice` are ignored.

### HTTP Request

`PUT https://app.seventime.se/api/2/machineTimeLogs/`

### PUT Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                 | String | Yes | Id of the machine time log
modifiedByUser      | String | Yes | Id of the user updating the machine time log
machine             | String | No  | Id of the machine
user                | String | No  | Id of the user the machine time log is registered for
time                | Number | No  | Registered time in hours. Must be a positive number
timestamp           | String | No  | Start date and time in ISO 8601 format
endTimestamp        | String | No  | End date and time in ISO 8601 format. Cannot be before `timestamp`
customer            | String | No  | Id of the customer
project             | String | No  | Id of the project
workOrder           | String | No  | Id of the work order
department          | String | No  | Id of the department
resultUnit          | String | No  | Id of the result unit
costAccount         | String | No  | Id of the cost account
description         | String | No  | Description
internalDescription | String | No  | Internal description
isInvoiceable       | Boolean | No | If the machine time log is invoiceable
supplementOrder     | Boolean | No | If the machine time log is a supplement order

<aside class="warning">
The fields <code>price</code> and <code>pricePerHour</code> cannot be set. The price is calculated from the machine's price per hour.
</aside>

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

> The above command returns JSON structured like this:

```json
{
  "_id": "65a50f80d1e44854f9c12345"
}
```

This endpoint deletes a machine time log. A machine time log that has been invoiced cannot be deleted.

### HTTP Request

`DELETE https://app.seventime.se/api/2/machineTimeLogs/`

### DELETE Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id             | String | Yes | Id of the machine time log
deletedByUser   | String | Yes | Id of the user who deleted the machine time log
