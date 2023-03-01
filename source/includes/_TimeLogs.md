# Time Logs
## Get Time Logs


```shell
curl "https://app.seventime.se/api/2/timeLogs/?limit=3&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/timeLogs/?limit=3&page=1";
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
    "totalResources": 1182,
    "totalPages": 394,
    "currentPage": 1
  },
  "data": [
    {
      "_id": "514959f8733259db75648975215",
      "allDay": false,
      "cost": 10690.5824,
      "createDate": "2013-03-16T11:39:36.437Z",
      "customer": null,
      "description": "",
      "endTimestamp": "2013-03-16T11:39:35.000Z",
      "isWorkTime": true,
      "project": null,
      "status": 1,
      "time": 41.18577972222222,
      "timeCategory": null,
      "timestamp": "2013-03-14T18:28:26.193Z",
      "user": "51203146506d961c030798526587",
      "userName": "Anna Andersson",
      "invoiceableTime": 41.18577972222222,
      "customFields": [],
      "isInvoiceable": true,
      "isInvoiced": false,
      "machineTimePrices": [],
      "machineTimeSupplements": [],
      "realTimestamp": "2020-08-27T07:52:57.685Z",
      "startLocation": {
        "coordinates": [],
        "type": "Point"
      },
      "stopLocation": {
        "coordinates": [],
        "type": "Point"
      },
      "unSocialHoursCosts": [
        {
          "_id": "5f57385dbe6f05476e5923541",
          "salaryType": "58cb7f24e9c363d0b0a1258984",
          "salaryTypeName": "OB kväll",
          "costPerHour": 150,
          "time": 6
        },
        {
          "_id": "5f57385dbe6f054764875216",
          "salaryType": "58cb7f24e9c363d0b689847a",
          "salaryTypeName": "OB kväll",
          "costPerHour": 150,
          "time": 10.5261325
        }
      ]
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves time logs (and absences if the punch clock module is not used). The attribute "isAbsence" will be true for absences.

### HTTP Request

`GET https://app.seventime.se/api/2/timeLogs`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
user               |  | If specified, time logs that match the parameter will be included.
customer           |  | If specified, time logs that match the parameter will be included.
project            |  | If specified, time logs that match the parameter will be included.
task               |  | If specified, time logs that match the parameter will be included.
category           |  | If specified, time logs that match the parameter will be included.
workOrder          |  | If specified, time logs that match the parameter will be included.
workOrderNumber    |  | If specified, time logs that match the parameter will be included.
timestamp          |  | If specified, time logs that start after the given date and time will be included. Accepted formats: 'YYYY-MM-HH HH:MM', 'YYYY-MM-HH HH:MM:SS', 'YYYY-MM-HHTHH:MM', 'YYYY-MM-HHTHH:MM:SS'
endTimestamp       |  | If specified, time logs that end before the given date and time will be included. Accepted formats: 'YYYY-MM-HH HH:MM', 'YYYY-MM-HH HH:MM:SS', 'YYYY-MM-HHTHH:MM', 'YYYY-MM-HHTHH:MM:SS'
invoicedDate       |  | If specified, time logs with invoice date since the specified timestamp will be included. Accepted formats: 'YYYY-MM-HH HH:MM', 'YYYY-MM-HH HH:MM:SS', 'YYYY-MM-HHTHH:MM', 'YYYY-MM-HHTHH:MM:SS'
isAbsence          |  | If specified, time logs that is of "absence type" will be included.
lastModified       |  | If specified, time logs that has been modified since the specified timestamp will be included. Accepted formats: 'YYYY-MM-HH HH:MM', 'YYYY-MM-HH HH:MM:SS', 'YYYY-MM-HHTHH:MM', 'YYYY-MM-HHTHH:MM:SS'
sortBy             |  | If specified, a sort will be made on the specified parameter
sortDirection      |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending





## Get a specific Time Log

```shell
curl "https://app.seventime.se/api/2/timeLogs/514959f8733259db45897213548" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/timeLogs/514959f8733259db45897213548";
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
    "startLocation": {
      "type": "Point",
      "coordinates": []
    },
    "stopLocation": {
      "type": "Point",
      "coordinates": []
    },
    "allDay": false,
    "status": 1,
    "isInvoiceable": true,
    "isInvoiced": false,
    "_id": "514959f8733259db45897213548",
    "cost": 10690.5824,
    "createDate": "2013-03-16T11:39:36.437Z",
    "customer": null,
    "description": "",
    "endTimestamp": "2013-03-16T11:39:35.000Z",
    "isWorkTime": true,
    "project": null,
    "time": 41.18577972222222,
    "timeCategory": null,
    "isAbsence": false,
    "timestamp": "2013-03-14T18:28:26.193Z",
    "user": "51203146506d961c030248975612",
    "userName": "Anna Andersson",
    "invoiceableTime": 41.18577972222222,
    "customFields": [],
    "machineTimePrices": [],
    "machineTimeSupplements": [],
    "realTimestamp": "2020-08-27T07:52:57.685Z",
    "unSocialHoursCosts": [
      {
        "_id": "5f57385dbe6f05368974521",
        "salaryType": "58cb7f24e9c363d4589761258",
        "salaryTypeName": "OB kväll",
        "costPerHour": 150,
        "time": 6
      },
      {
        "_id": "5f57385dbe6f054765879125",
        "salaryType": "58cb8f2e9c663d0e68482a",
        "salaryTypeName": "OB kväll",
        "costPerHour": 150,
        "time": 10.5261325
      }
    ]
  }
}
```

This endpoint retrieves a specific time log.

### HTTP Request

`GET https://app.seventime.se/api/2/timeLogs/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the time log to retrieve

## Get Time Categories

```shell
curl "https://app.seventime.se/api/2/timeCategories" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/timeCategories/?";
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
      "_id": "58cd3c4771b8a3c34658974521",
      "name": "Semester",
      "description": "",
      "isAbsenceType": true,
      "isUnsocialHour": false,
      "isInvoiceable": true,
      "pricePerHour": 0,
      "articleNumber": "040",
      "isWorkTime": true,
      "isActive": true,
      "color": "FF9800",
      "isVacation": true,
      "presenceCode": "",
      "requirePreAttest": true,
      "isMachineTime": false
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves time categories.

### HTTP Request

`GET https://app.seventime.se/api/2/timeCategories`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy             |  | If specified, a sort will be made on the specified parameter
sortDirection      |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get a specific Time Category

```shell
curl "https://app.seventime.se/api/2/timeCategories/58cd3c4771b8a3c34658974521" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/timeCategories/58cd3c4771b8a3c34658974521";
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
    "_id": "58cd3c4771b8a3c34658974521",
    "name": "Semester",
    "description": "",
    "isAbsenceType": true,
    "isUnsocialHour": false,
    "isInvoiceable": true,
    "pricePerHour": 0,
    "articleNumber": "040",
    "isWorkTime": true,
    "isActive": true,
    "color": "FF9800",
    "isVacation": true,
    "presenceCode": "",
    "requirePreAttest": true,
    "isMachineTime": false
  }
}
```

This endpoint retrieves a specific time category.



### HTTP Request

`GET https://app.seventime.se/api/2/timeCategories/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the time category to retrieve


## Create a Time Log

```shell
curl -X POST "https://app.seventime.se/api/2/timeLogs/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"createdByUser":"5f48eb3e65d7ee4926574851","user":"51203146506d961c03036589741","timestamp":"2020-06-05 12:00","time":"5"}'
```

```javascript
let jsonData = {
  createdByUser: '5f48eb3e65d7ee4926574851',
  user: '51203146506d961c03036589741',
  timestamp: '2020-06-05 12:00',
  time: '5'
};

let options = {
  url: 'https://app.seventime.se/api/2/timeLogs',
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
    console.error("ERROR! Unable to create time log: " + error);
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
```

This endpoint creates a time log

### HTTP Request

`POST https://app.seventime.se/api/2/timeLogs/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
createdByUser       | String | Yes | Id of the user who created the time log
user                | String | Yes | Id of the user on the time log
timestamp           | String | Yes | Starting date and time for the time log. Accepted formats: 'YYYY-MM-HH HH:MM', 'YYYY-MM-HH HH:MM:SS', 'YYYY-MM-HHTHH:MM', 'YYYY-MM-HHTHH:MM:SS'
endTimestamp        | String | No* | Starting date and time for the time log. Accepted formats: 'YYYY-MM-HH HH:MM', 'YYYY-MM-HH HH:MM:SS', 'YYYY-MM-HHTHH:MM', 'YYYY-MM-HHTHH:MM:SS'. *This is required if field 'time' is not specified
time                | String | No* | Time of the time log in hours. *This is required if field 'endTimestamp' is not specified
invoiceableTime     | String | No  | Invoiceable time. If not specified, this will be set to the time of the time log
customer            | String | No  | Id of the customer
project             | String | No  | Id of the project
timeCategory        | String | No  | Id of the time category
workOrder           | String | No  | Id of the work order
pricePerHour        | Number | No  | price per hour of the time log. If not specified, the price will be set according to the user, customer, project, time category or work order.
description         | String | No  | Description/notes of the time log
internalDescription | String | No  | Internal description/notes of the time log
supplementOrder     | Boolean | No  | Is the time log a supplement order?
isInvoiceable       | Boolean | No  | Invoiceable ot not
isAbsence           | Boolean | No  | Should be set to true if it is an absence  

## Update a Time Log

```shell
curl -X PUT "https://app.seventime.se/api/2/timeLogs/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fbcfe75ba9312280e2145897521","modifiedByUser":"51718241fdb708f3923268","user":"51203146506d961c03036589741","timestamp":"2020-10-7 07:00","endTimestamp":"2020-10-7 15:00"}'
```

```javascript
let jsonData = {
  _id: '5fbcfe75ba9312280e2145897521',
  modifiedByUser: '51718241fdb708f3923268',
  user: '51203146506d961c03036589741',
  timestamp: '2020-10-07 07:00',
  endTimestamp: '2020-10-07 15:00',
};

let options = {
  url: 'https://app.seventime.se/api/2/timeLogs',
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
    console.log("Time log updated: _id: " + body._id);
  } else {
    console.error("ERROR! Unable to update time log: " + error);
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
  "isAbsence": false,
  "_id": "5fbcfe75ba9312280e2145897521",
  "timestamp": "2020-10-07T06:00:00.000Z",
  "realTimestamp": "2020-10-07T06:00:00.000Z",
  "createDate": "2020-11-24T12:37:09.258Z",
  "unSocialHoursCosts": [],
  "customFields": [],
  "machineTimePrices": [],
  "machineTimeSupplements": [],
  "user": "51203146506d961c03036589741",
  "userName": "Anna Andersson",
  "endTimestamp": "2020-10-07T014:00:00.000Z",
  "realEndTimestamp": "2020-10-07T14:00:00.000Z",
  "time": 8,
  "invoiceableTime": 8,
  "pricePerHour": 777,
  "price": 777
}
"Time log updated: _id: 5fbcfe75ba9312280ef6523e"
```

This endpoint updates a time log

### HTTP Request

`PUT https://app.seventime.se/api/2/timeLogs/`

### PUT Parameters
The table below shows the required fields. Other available fields can be found in the section 'Create a Time Log'.

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id             | String | Yes | Id of the time log
modifiedByUser  | String | Yes | Id of the user who made the change
user            | String | Yes | Id of the user on the time log

## Delete a Time Log

```shell
curl -X DELETE "https://app.seventime.se/api/2/timeLogs/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"51203146506d961c35798485","deletedByUser":"51203146506d961c03036589741"}'
```

```javascript
let jsonData = {
  _id: '51203146506d961c35798485',
  deletedByUser: '51203146506d961c03036589741'
};

let options = {
  url: 'https://app.seventime.se/api/2/timeLogs',
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
    console.log("Time log deleted: _id: " + body._id);
  } else {
    console.error("ERROR! Unable to delete time log: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "_id": "51203146506d961c35798485"
}
"Time log deleted: _id: 51203146506d961c35798485"
```

This endpoint deletes a time log

### HTTP Request

`DELETE https://app.seventime.se/api/2/timeLogs/`

### DELETE Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id             | String | Yes | Id of the time log
