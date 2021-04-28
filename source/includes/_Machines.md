# Machines
## Get Machines


```shell
curl "https://app.seventime.se/api/2/machines/?limit=10&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/machines/?limit=10&page=1";
let options = {
  url: url,
  headers: {
    "Client-Secret": "thisismysecretkey"
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
    "totalResources": 30,
    "totalPages": 3,
    "currentPage": 2
  },
  "data": [
    {
      "_id": "5a4bc02e40a13d71799764283",
      "lastHoursUsedRegDate": "2020-09-27T12:06:19.225Z",
      "hoursUsed": 5193,
      "lastMileageRegDate": "2020-09-27T12:06:19.225Z",
      "mileage": 10122.7,
      "isActive": true,
      "createdByUserName": "Anna Andersson",
      "createdByUser": "5113986056b831a917962158",
      "hoursCanBeRegistered": true,
      "canBePlanned": true,
      "isInvoiceable": true,
      "serialNumber": "846821",
      "machineModel": "ME500",
      "machineNumber": "21",
      "machineName": "EWR150E-21",
      "trackunitData": {
        "id": "1135803"
      },
      "modifiedDate": "2020-09-27T12:06:19.225Z",
      "createDate": "2018-01-02T17:37:02.629Z",
      "machineLog": [],
      "documents": [],
      "articleNumber": "",
      "machineType": null,
      "machineTypeName": "",
      "machineGroup": "",
      "purchaseDate": null,
      "serviceable": false,
      "serviceIntervalInKm": 0,
      "serviceIntervalInHours": 0,
      "serviceIntervalInMonths": 0,
      "mileageLastService": 0,
      "hoursLastService": 0,
      "lastServiceDate": null,
      "unitPrice": 0,
      "unitCost": 0,
      "distributor": null,
      "distributorName": "",
      "customFields": [],
      "debitManualRegistrationPrices": [],
      "debitMinimiPrices": [],
      "debitSchedulePrices": [],
      "isSupplementForMachines": []
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves machines.

### HTTP Request

`GET https://app.seventime.se/api/2/machines`

### Query Parameters

E.g. `https://app.seventime.se/api/2/machines/?machineNumber=21`

Parameter | Default | Description
--------- | ------- | -----------
name             |  | If specified, invoices that match the parameter will be included.
machineNumber    |  | If specified, invoices that match the parameter will be included.
machineTypeName  |  | If specified, invoices that match the parameter will be included.
machineModel     |  | If specified, invoices that match the parameter will be included.
serialNumber     |  | If specified, invoices that match the parameter will be included.
serviceable      |  | If specified, invoices that match the parameter will be included.
sortBy           |  | If specified, a sort will be made on the specified parameter
sortDirection    |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending




## Get a specific Machine

```shell
curl "https://app.seventime.se/api/2/machines/5a4bc02e40a13d71799764283" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/machines/5a4bc02e40a13d71799764283";
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
    "trackunitData": {
      "id": "1135803"
    },
    "machineLog": [],
    "isSupplementForMachines": [],
    "_id": "5a4bc02e40a13d71799764283",
    "lastHoursUsedRegDate": "2020-09-27T12:06:19.225Z",
    "hoursUsed": 5193,
    "lastMileageRegDate": "2020-09-27T12:06:19.225Z",
    "mileage": 10122.7,
    "isActive": true,
    "createdByUserName": "Anna Andersson",
    "createdByUser": "5113986056b831a96489527",
    "hoursCanBeRegistered": true,
    "canBePlanned": true,
    "isInvoiceable": true,
    "serialNumber": "846821",
    "machineModel": "ME500",
    "machineNumber": "21",
    "machineName": "EWR150E-21",
    "modifiedDate": "2020-09-27T12:06:19.225Z",
    "createDate": "2018-01-02T17:37:02.629Z",
    "documents": [],
    "articleNumber": "",
    "machineType": null,
    "machineTypeName": "",
    "machineGroup": "",
    "purchaseDate": null,
    "serviceable": false,
    "serviceIntervalInKm": 0,
    "serviceIntervalInHours": 0,
    "serviceIntervalInMonths": 0,
    "mileageLastService": 0,
    "hoursLastService": 0,
    "lastServiceDate": null,
    "unitPrice": 0,
    "unitCost": 0,
    "distributor": null,
    "distributorName": "",
    "customFields": [],
    "debitManualRegistrationPrices": [],
    "debitMinimiPrices": [],
    "debitSchedulePrices": []
  }
}
```

This endpoint retrieves a specific machine.



### HTTP Request

`GET https://app.seventime.se/api/2/machine/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the machine to retrieve

## Get Machine Types

```shell
curl "https://app.seventime.se/api/2/machineTypes/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/machineTypes/";
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
      "_id": "57e89fbae191f8ba548916",
      "name": "Fordon",
      "isActive": true,
      "createDate": "2017-10-19T12:50:50.361Z"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves machine types.



### HTTP Request

`GET https://app.seventime.se/api/2/machineTypes/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending
