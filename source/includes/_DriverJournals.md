# Driver Journals
## Get Driver Journals

```shell
curl "https://app.seventime.se/api/2/driverJournals/?fromDate=2016-06-01&toDate=2016-06-30&limit=5&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/driverJournals/?fromDate=2016-06-01&toDate=2016-06-30&limit=5&page=1";
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
    "totalResources": 87,
    "totalResourcesIsExact": true,
    "totalPages": 18,
    "currentPage": 2,
    "hasMore": true,
    "nextPage": 3
  },
  "data": [
    {
      "_id": "5613c0eaa1b2c3d4e5001026",
      "name": "",
      "driverJournalItemType": "574ed842a1b2c3d4e5001027",
      "driverJournalItemTypeName": "4 kr/km",
      "car": null,
      "carRegistrationNumber": "ABC123",
      "description": "",
      "user": "5f48eb3ea1b2c3d4e5001028",
      "userName": "Anna Andersson",
      "customer": "5bb26376a1b2c3d4e5001029",
      "customerName": "Company AB",
      "project": "5f924f4fa1b2c3d4e5001030",
      "projectName": "Tester",
      "workOrder": "5bae34dca1b2c3d4e5001031",
      "workOrderTitle": "20160525",
      "workOrderNumber": 1181,
      "startAddress": "Östra Gatan 129, Stockholm",
      "endAddress": "Västra Gatan 921, Stockholm",
      "travelPurpose": ".",
      "startOdometer": 156,
      "endOdometer": 178,
      "totalDistance": 22,
      "price": 4,
      "totalAmount": 88,
      "isInvoiced": true,
      "invoice": "5fab29b0a1b2c3d4e5001032",
      "modifiedDate": "2016-06-17T09:29:01.958Z",
      "createDate": "2016-06-17T09:20:46.845Z",
      "isInvoiceable": true,
      "timestamp": "2016-06-17T09:20:10.254Z"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves driver journals.

At least one filter, e.g. a date range or a user, has to be specified. A request without any filter returns HTTP status 422 with the code `QUERY_TOO_BROAD`.

The result is paginated. `meta.totalResources` is capped at 2000; if there are more matching driver journals, `meta.totalResourcesIsExact` is false and `meta.totalPages` is null. Use `meta.hasMore` and `meta.nextPage` to fetch the next page.

### HTTP Request

`GET https://app.seventime.se/api/2/driverJournals`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
user                        |  | If specified, driver journals for the user with this id will be included.
project                     |  | If specified, driver journals for the project with this id will be included.
customer                    |  | If specified, driver journals for the customer with this id will be included.
workOrder                   |  | If specified, driver journals for the work order with this id will be included.
driverJournalItemTypeName   |  | If specified, driver journals that match the parameter will be included.
isInvoiceable               |  | If specified, driver journals that match the parameter will be included.
workOrderNumber             |  | If specified, driver journals that match the parameter will be included.
carRegistrationNumber       |  | If specified, driver journals that match the parameter will be included.
startAddress                |  | If specified, driver journals that match the parameter will be included.
endAddress                  |  | If specified, driver journals that match the parameter will be included.
fromDate                    |  | If specified, driver journals registered after or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
toDate                      |  | If specified, driver journals registered before or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
sortBy                      | timestamp | If specified, a sort will be made on the specified parameter
sortDirection               |  | "ascending" or "descending". The sort order will be ascending or descending
limit                       | 100 | Number of driver journals per page. Maximum 500
page                        | 1 | Page number




## Get a specific Driver Journal

```shell
curl "https://app.seventime.se/api/2/driverJournals/5613c0eaa1b2c3d4e5001033" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/driverJournals/5613c0eaa1b2c3d4e5001033";
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
    "isInvoiceable": true,
    "_id": "5613c0eaa1b2c3d4e5001033",
    "name": "",
    "driverJournalItemType": "574ed842a1b2c3d4e5001034",
    "driverJournalItemTypeName": "4 kr/km",
    "car": null,
    "carRegistrationNumber": "ABC123",
    "description": "",
    "user": "5f48eb3ea1b2c3d4e5001035",
    "userName": "Anna Andersson",
    "customer": "5bb26376a1b2c3d4e5001036",
    "customerName": "Company AB",
    "project": "5f924f4fa1b2c3d4e5001037",
    "projectName": "Tester",
    "workOrder": "5bae34dca1b2c3d4e5001038",
    "workOrderTitle": "20160525",
    "workOrderNumber": 1181,
    "startAddress": "Östra Gatan 129, Stockholm",
    "endAddress": "Västra Gatan 921, Stockholm",
    "travelPurpose": ".",
    "startOdometer": 156,
    "endOdometer": 178,
    "totalDistance": 22,
    "price": 4,
    "totalAmount": 88,
    "isInvoiced": true,
    "invoice": "5fab29b0a1b2c3d4e5001039",
    "modifiedDate": "2016-06-17T09:29:01.958Z",
    "createDate": "2016-06-17T09:20:46.845Z",
    "timestamp": "2016-06-17T09:20:10.254Z"
  }
}
```

This endpoint retrieves a specific driver journal.


### HTTP Request

`GET https://app.seventime.se/api/2/driverJournals/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the driver journal to retrieve

## Get Driver Journals Types

```shell
curl "https://app.seventime.se/api/2/driverJournalTypes" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/driverJournalTypes";
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
      "_id": "5e5ef41fa1b2c3d4e5001040",
      "name": "Diesel - ej skt.fri",
      "articleNumber": "45",
      "cost": 0.5,
      "price": 0.65,
      "isInvoiceable": true,
      "isDefault": false,
      "salaryCompensationType": 20,
      "salaryType": "5e5cd96da1b2c3d4e5001041",
      "salaryTypeName": "Milersättning för diesel",
      "createDate": "2020-03-03T09:14:11.750Z",
      "isActive": true,
      "salaryCode": "9172"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves driver journals types.

### HTTP Request

`GET https://app.seventime.se/api/2/driverJournalTypes`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy                      |  | If specified, a sort will be made on the specified parameter
sortDirection               |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


## Create a Driver Journal

```shell
curl -X POST "https://app.seventime.se/api/2/driverJournals/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"createdByUser":"51203146a1b2c3d4e5001042","user":"5f48eb3ea1b2c3d4e5001043","carRegistrationNumber":"ABC123","driverJournalItemType":"5e5ef4124135975","startAddress":"Address start, Stockholm","endAddress":"Address end, Stockholm","travelPurpose":"Delivery","startOdometer":45,"endOdometer":60}'
```

```javascript
let jsonData = {
  createdByUser: '51203146a1b2c3d4e5001042',
  user: '5f48eb3ea1b2c3d4e5001043',
  carRegistrationNumber: 'ABC123',
  driverJournalItemType: '5e5ef4124135975',
  startAddress: 'Address start, Stockholm',
  endAddress: 'Address end, Stockholm',
  travelPurpose: 'Delivery',
  startOdometer: '45',
  endOdometer: '60',
};

let options = {
  url: 'https://app.seventime.se/api/2/driverJournals',
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
    console.log("Driver journal created: _id: " + body._id);

  } else {
    console.error("ERROR! Unable to create driver journal: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "isInvoiceable": true,
  "_id": "5fc619b9a1b2c3d4e5001044",
  "timestamp": "2020-12-01T10:23:53.370Z",
  "createDate": "2020-12-01T10:23:53.370Z",
  "modifiedDate": "2020-12-01T10:23:53.370Z",
  "user": "5f48eb3ea1b2c3d4e5001045",
  "userName": "Anna Andersson",
  "carRegistrationNumber": "ABC123",
  "driverJournalItemType": "5e5ef41fa1b2c3d4e5001046",
  "driverJournalItemTypeName": "Diesel - ej skt.fri",
  "startAddress": "Address start, Stockholm",
  "endAddress": "Address end, Stockholm",
  "travelPurpose": "Delivery",
  "startOdometer": 45,
  "endOdometer": 60,
  "totalDistance": 15,
  "isSalaryCompensated": false,
  "price": 0,
  "totalAmount": 0,
  "cost": 0,
  "totalCost": 0
}
"Driver journal created: _id: 5fc619b9a1b2c3d4e5001047"
```

This endpoint creates a driver journal

### HTTP Request

`POST https://app.seventime.se/api/2/driverJournals/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
createdByUser           | String | Yes | Id of the user who created the driver journal
user                    | String | Yes | Id of the user on the driver journal
vehicle                 | String | Yes*| Id of the vehicle. *Required if carRegistrationNumber is not specified
carRegistrationNumber   | String | Yes*| Car registration number. *Required if vehicle is not specified. This will not be used if vehicle is specified
driverJournalItemType   | String | Yes | Type of trip
startAddress            | String | Yes | Start address of the driver journal
endAddress              | String | Yes | End address of the driver journal
travelPurpose           | String | Yes | Errand/position/Company/Contact person
startOdometer           | Number | Yes | Odometer reading at the start
endOdometer             | Number | Yes | Odometer reading at the end
customer                | String | No  | Id of the customer
project                 | String | No  | Id of the project
workOrder               | String | No  | Id of the work order. If project is specified, the work order must belong to the project. The customer from the work order will be used on the driver journal
price                   | Number | No  | Price/km
cost                    | Number | No  | Cost/km
description             | String | No  | Description or notes on the driver journal
isInvoiceable           | Boolean | No | Is the driver jounal invoiceable? If not specified, this will be set to true
isSalaryCompensated     | Boolean | No | Is the driver jounal salary compensated? If not specified, this will be set to false

## Update a Driver Journal

```shell
curl -X PUT "https://app.seventime.se/api/2/driverJournals/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fc619b9a1b2c3d4e5001048","modifiedByUser":"51203146a1b2c3d4e5001049","user":"5f48eb3ea1b2c3d4e5001050"}'
```

```javascript
let jsonData = {
  _id: '5fc619b96294735fc7812458',
  modifiedByUser: '51203146a1b2c3d4e5001051',
  user: '5f48eb3ea1b2c3d4e5001052'
};

let options = {
  url: 'https://app.seventime.se/api/2/driverJournals',
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
    console.log("Driver journal updated: _id: " + body._id);
  } else {
    console.error("ERROR! Unable to update driver journal: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "isInvoiceable": true,
  "_id": "5fc619b9a1b2c3d4e5001053",
  "timestamp": "2020-12-01T10:23:53.370Z",
  "createDate": "2020-12-01T10:23:53.370Z",
  "modifiedDate": "2020-12-01T10:23:53.370Z",
  "user": "5f48eb3ea1b2c3d4e5001054",
  "userName": "Anna Andersson",
  "carRegistrationNumber": "ABC123",
  "driverJournalItemType": "5e5ef41fa1b2c3d4e5001055",
  "driverJournalItemTypeName": "Diesel - ej skt.fri",
  "startAddress": "Address start, Stockholm",
  "endAddress": "Address end, Stockholm",
  "travelPurpose": "Delivery",
  "startOdometer": 45,
  "endOdometer": 60,
  "totalDistance": 15,
  "isSalaryCompensated": false,
  "price": 0,
  "totalAmount": 0,
  "cost": 0,
  "totalCost": 0
}
"Driver journal updated: _id: 5fc619b9a1b2c3d4e5001053"
```

This endpoint updates a driver journal

### HTTP Request

`PUT https://app.seventime.se/api/2/driverJournals/`

### PUT Parameters
The table below shows the required fields. Other available fields can be found in the section 'Create a Driver Journal'.

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id            | String | Yes | Id of the driver journal
modifiedByUser | String | Yes | Id of the user who made the change
user           | String | Yes | Id of the user on the driver journal

## Delete a Driver Journal

```shell
curl -X DELETE "https://app.seventime.se/api/2/driverJournals/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fc619b9a1b2c3d4e5001056","deletedByUser":"51203146a1b2c3d4e5001057"}'
```

```javascript
let jsonData = {
  _id: '5fc619b9a1b2c3d4e5001058',
  deletedByUser: '51203146a1b2c3d4e5001059'
};

let options = {
  url: 'https://app.seventime.se/api/2/driverJournals',
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
    console.log("Driver journal deleted: _id: " + body._id);
  } else {
    console.error("ERROR! Unable to delete driver journal: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "_id": "5fc619b9a1b2c3d4e5000507",
  "name": ""
}
"Driver journal deleted: _id: 5fc619b9a1b2c3d4e5001060"
```

This endpoint deletes a driver journal. A driver journal that has been invoiced or salary processed cannot be deleted.

### HTTP Request

`DELETE https://app.seventime.se/api/2/driverJournals/`

### DELETE Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                    | String | Yes | Id of the driver journal
deletedByUser          | String | Yes | Id of the user who deleted the driver journal
