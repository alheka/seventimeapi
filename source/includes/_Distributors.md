# Distributors
## Get Distributors

```shell
curl "https://app.seventime.se/api/2/distributors/?limit=5&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/distributors/?limit=5&page=1";
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
    "totalResources": 16,
    "totalPages": 4,
    "currentPage": 3
  },
  "data": [
    {
      "_id": "5f6b2e6af24d5df55b69277",
      "name": "UE lev 20200923",
      "distributorNumber": "20",
      "address": "",
      "zipCode": "",
      "city": "",
      "country": "",
      "phone": "",
      "email": "",
      "organizationNumber": "",
      "notes": "",
      "purchaseOrderEmail": "",
      "ourCustomerNumber": "",
      "paymentDays": 30,
      "hasSelfBilling": true,
      "selfBillingSettings": {
        "invoiceDeduction": 5,
        "deductionExpenseItem": "5e74bf0917ae9b9166f5b4b9",
        "invoiceNumberSeries": "UELEV23",
        "invoiceCounter": 1,
        "emailForSelfBilling": "tommy@seventime.se"
      },
      "isActive": true,
      "isSubContractor": true,
      "createdDate": "2020-09-23T13:19:42.450Z",
      "modifiedDate": "2020-09-23T13:19:42.450Z",
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves distributors.

### HTTP Request

`GET https://app.seventime.se/api/2/distributors`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
name                        |  | If specified, distributors that match the parameter will be included.
sortBy                      |  | If specified, a sort will be made on the specified parameter
sortDirection               |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


## Get a specific Distributor

```shell
curl "https://app.seventime.se/api/2/distributors/5f6b2e6af24d5df55b69277" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/distributors/5f6b2e6af24d5df55b69277";
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
    "selfBillingSettings": {
      "invoiceDeduction": 5,
      "deductionExpenseItem": "5e74bf0917ae9b9166f5b4b9",
      "invoiceNumberSeries": "UELEV23",
      "invoiceCounter": 1,
      "emailForSelfBilling": "tommy@seventime.se"
    },
    "_id": "5f6b2e6af24d5df55b69277",
    "name": "UE lev 20200923",
    "distributorNumber": "20",
    "address": "",
    "zipCode": "",
    "city": "",
    "country": "",
    "phone": "",
    "email": "",
    "organizationNumber": "",
    "notes": "",
    "purchaseOrderEmail": "",
    "ourCustomerNumber": "",
    "paymentDays": 30,
    "hasSelfBilling": true,
    "isActive": true,
    "isSubContractor": true,
    "createdDate": "2020-09-23T13:19:42.450Z",
    "modifiedDate": "2020-09-23T13:19:42.450Z",
    "systemAccount": "5112826056d961c030000001",
  }
}
```

This endpoint retrieves a specific distributor.


### HTTP Request

`GET https://app.seventime.se/api/2/distributors/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the distributor to retrieve


## Get Distributor Contact Persons

```shell
curl "https://app.seventime.se/api/2/distributorContactPersons/?distributor=5fca23df0317c3dae47b04a" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/distributorContactPersons/?distributor=5fca23df0317c3dae47b04a";
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
      "_id": "5fca23df0317c3dae47b04a",
      "name": "Kontaktperson 1",
      "title": "",
      "workPhone": "",
      "cellPhone": "",
      "email": "",
      "distributor": "5f6b2e6af24d5df55b69277",
      "distributorName": "UE lev 20200923",
      "mainContact": false,
      "isActive": true,
      "createdDate": "2020-12-04T10:13:03.965Z",
      "modifiedDate": "2020-12-04T10:13:03.965Z",
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves distributor contact persons.

### HTTP Request

`GET https://app.seventime.se/api/2/distributorContactPersons/?distributor=5fca23df0317c3dae47b04a`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
distributor                 |  | Id of the distributor. This field must be included
sortBy                      |  | If specified, a sort will be made on the specified parameter
sortDirection               |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending
