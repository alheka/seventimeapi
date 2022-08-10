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
      "_id": "5f6b2e6af24d5df526848",
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
        "deductionExpenseItem": "5e74bf0917ae9b91662484d",
        "invoiceNumberSeries": "UELEV23",
        "invoiceCounter": 1,
        "emailForSelfBilling": "email@company.com"
      },
      "isActive": true,
      "isSubContractor": true,
      "createdDate": "2020-09-23T13:19:42.450Z",
      "modifiedDate": "2020-09-23T13:19:42.450Z"
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
curl "https://app.seventime.se/api/2/distributors/5f6b2e6af24d5d7121b" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/distributors/5f6b2e6af24d5d7121b";
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
      "deductionExpenseItem": "5e74bf0917ae9b9166154952d",
      "invoiceNumberSeries": "UELEV23",
      "invoiceCounter": 1,
      "emailForSelfBilling": "email@company.com"
    },
    "_id": "5f6b2e6af24d5d7121b",
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
    "modifiedDate": "2020-09-23T13:19:42.450Z"
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
curl "https://app.seventime.se/api/2/distributorContactPersons/?distributor=5f6b2e6af24d5d7121b" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/distributorContactPersons/?distributor=5f6b2e6af24d5d7121b";
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
      "_id": "5fca23df0317c151d15459",
      "name": "Kontaktperson 1",
      "title": "",
      "workPhone": "",
      "cellPhone": "",
      "email": "",
      "distributor": "5f6b2e6af24d5d7121b",
      "distributorName": "UE lev 20200923",
      "mainContact": false,
      "isActive": true,
      "createdDate": "2020-12-04T10:13:03.965Z",
      "modifiedDate": "2020-12-04T10:13:03.965Z"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves distributor contact persons.

### HTTP Request

`GET https://app.seventime.se/api/2/distributorContactPersons/?distributor=5f6b2e6af24d5d7121b`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
distributor                 |  | Id of the distributor. This field must be included
sortBy                      |  | If specified, a sort will be made on the specified parameter
sortDirection               |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


## Create a Distributor

```shell
curl -X POST "https://app.seventime.se/api/2/distributors/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"name":"DistributorName"}'
```

```javascript
let jsonData = {
  name: 'DistributorName'
};

let options = {
  url: 'https://app.seventime.se/api/2/distributors',
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
    console.error("ERROR! Unable to distributor: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "_id": '62f3a242ca38bbsce075249',
  "name": 'Distributor Test',
  "distributorNumber": '123456',
  "address": 'test 1',
  "zipCode": '12345',
  "city": 'Båstad',
  "country": 'SE',
  "phone": '0412412412',
  "email": '132312kewkewa',
  "organizationNumber": '12345688',
  "vatNumber": '90',
  "bankgiro": 'eeee',
  "plusgiro": 'bbbbb',
  "notes": 'testartestar testar',
  "purchaseOrderEmail": 'test@testing.com',
  "ourCustomerNumber": '031239',
  "paymentDays": 45,
  "isSubContractor": true,
  "hasSelfBilling": true,
  "selfBillingSettings": {
    "invoiceDeduction": 10,
    "invoiceNumberSeries": 'SE',
    "invoiceCounter": 12,
    "emailForSelfBilling": 'llllllll'
  },
  "isActive": false,
  "createdDate": '2022-08-10T12:49:26.716Z',
  "modifiedDate": '2022-08-10T12:49:26.718Z',
  "documents": [],
  __v: 0
}

```

This endpoint creates a distributor

### HTTP Request

`POST https://app.seventime.se/api/2/distributors/`

### POST Parameters

Parameter | Type    | Required? | Description
--------- |---------| ----------- | -----------
name                | String  | Yes | Name of the distributor
distributorNumber   | String  | No  | Distributor number
address             | String  | No  | Address of the distributor
zipCode             | String  | No  | Zip code of the distributor
city                | String  | No  | City of the distributor
country             | String  | No  | Country of the distributor
email               | Number  | No  | Email of the distributor
organizationNumber  | String  | No  | Organization number for the distributor
vatNumber           | String  | No  | VAT number for the distributor
bankgiro            | String  | No  | Bankgiro for distributor
plusgiro            | String  | No  | Plusgiro for distributor
notes               | String  | No  | Notes
purchaseOrderEmail  | String  | No  | The purchase order email
ourCustomerNumber   | String  | No  | Your customer number for the distributor
paymentDays         | Number  | No  | Number of payment days
isSubContractor     | Boolean | No  | Is it a sub contractor?
hasSelfBilling      | Boolean | No  | Should the distributor have self billing?
selfBillingSettings | Array   | No  | Array containing information about self billing. See below for more details.
isActive            | Boolean | No  | Should the distributor be active?

**Attributes for selfBillingSettings**

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
invoiceDeduction          | String | No | Invoice deduction
invoiceNumberSeries       | String | No | Invoice number series
invoiceCounter            | String | No | Invoice counter
emailForSelfBilling       | String | No | Email for self billing


## Update a Distributor

```shell
curl -X PUT "https://app.seventime.se/api/2/distributors/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"62f3a242ca38bbsce075249",name:"New distributor name"}'
```

```javascript
let jsonData = {
  _id: '5fbcfe75ba9312280e2145897521',
  name: 'New distributor name'
};

let options = {
  url: 'https://app.seventime.se/api/2/distributors',
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
    console.log("Distributor updated: _id: " + body._id);
  } else {
    console.error("ERROR! Unable to distributor: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "_id": '62f3a242ca38bbsce075249',
  "name": 'New distributor name',
  "distributorNumber": '123456',
  "address": 'test 1',
  "zipCode": '12345',
  "city": 'Båstad',
  "country": 'SE',
  "phone": '0412412412',
  "email": '132312kewkewa',
  "organizationNumber": '12345688',
  "vatNumber": '90',
  "bankgiro": 'eeee',
  "plusgiro": 'bbbbb',
  "notes": 'testartestar testar',
  "purchaseOrderEmail": 'test@testing.com',
  "ourCustomerNumber": '031239',
  "paymentDays": 45,
  "isSubContractor": true,
  "hasSelfBilling": true,
  "selfBillingSettings": {
    "invoiceDeduction": 10,
    "invoiceNumberSeries": 'SE',
    "invoiceCounter": 12,
    "emailForSelfBilling": 'llllllll'
  },
  "isActive": false,
  "createdDate": '2022-08-10T12:49:26.716Z',
  "modifiedDate": '2022-08-10T12:49:26.718Z',
  "documents": [],
  __v: 0
}
"Distributor updated: _id: 62f3a242ca38bbsce075249"
```

This endpoint updates a distributor

### HTTP Request

`PUT https://app.seventime.se/api/2/distributors/`

### PUT Parameters
The table below shows the required fields. Other available fields can be found in the section 'Create a Time Log'.

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id             | String | Yes | Id of the distributor
