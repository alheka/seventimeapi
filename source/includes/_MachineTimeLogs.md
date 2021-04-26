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
      "_id": "59ef428433092a4536000066",
      "time": 12,
      "invoiceableTime": 12,
      "description": "12",
      "internalDescription": "",
      "attestedBy": null,
      "invoice": null,
      "machine": "59e75917ae561db738700451",
      "machineName": "Grävare",
      "user": "51203146506d961c030791801",
      "userName": "Tommy Hellström",
      "department": "58b30abde244b75d46501274",
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
      "timestamp": "2017-10-24T13:39:06.144Z",
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
curl "https://app.seventime.se/api/2/machines/5a4bc02e40a13d7179005920" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/machines/5a4bc02e40a13d7179005920";
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
    "_id": "5a4bc02e40a13d7179005920",
    "time": 12,
    "invoiceableTime": 12,
    "description": "12",
    "internalDescription": "",
    "attestedBy": null,
    "invoice": null,
    "machine": "59e75917ae561db738700451",
    "machineName": "Grävare",
    "user": "51203146506d961c030791801",
    "userName": "Tommy Hellström",
    "department": "58b30abde244b75d46501274",
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
    "timestamp": "2017-10-24T13:39:06.144Z",
  }
}
```

This endpoint retrieves a specific machine time log.



### HTTP Request

`GET https://app.seventime.se/api/2/machineTimeLog/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the machine time log to retrieve
