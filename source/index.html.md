---
title: Seven Time API Reference


language_tabs: # must be one of https://git.io/vQNgJ
- shell
- javascript

toc_footers:
- <a href="https://seventime.se">Seven Time</a>

includes:
- errors

search: true
---

# Introduction

Welcome to the Seven Time API! You can use our API to access Seven Time API endpoints, currently limited to customers.

You can view code examples for Shell and JavaScript in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Send Client-Secret in the header. Sample with the request library */

let options = {
  headers: {
    "Client-Secret": "thisismysecretkey",
    "Content-Type": "application/json",
    "Accept": 'application/json'
  }
};

request.post(options, function (error, response, body) {
  // ....
});

```

> Make sure to replace `thisismysecretkey` with your API key.

Seven Time uses API keys to allow access to the API. You can get a new Seven Time API key in **"Settings -> Integrations -> API"** in Seven Time.

Seven Time expects the API key to be included in all API requests to the server in a header that looks like the following:

`Client-Secret: thisismysecretkey`

<aside class="notice">
You must replace <code>thisismysecretkey</code> with your personal API key.
</aside>

# Header fields
In addition to the 'Client-Secret', a few fields are required in the Header:

- Content-type - Must be "application/json"
- Accept - Must be "application/json"

# Actions
The Seven Time API supports three different actions:

- get - used to retrieve data
- push - used to create new items, e.g. new customers, users, etc.
- put - used to update items, e.g. update an exisiting customer, user, etc.

# Pagination
Searches that returns a large number of results are paged due to performance reasons. These searches are limited by the parameter 'limit'. 

This parameter limits the number of results that will be returned. By default, this limit is set to 100 but can be set as low as 1 and as high as 500.

When the number of results exceed the given limit, the 'page' parameter can be used to retrieve different intervals in the data.

## Example of 'limit' and 'page'
A search returns 490 results and the limit is set to 100. To get the first 100 results, the parameter 'page' is set to 1. To get the next 100 results, 'page' is set to 2, etc.


# Customers

## Get Customers


```shell
curl "https://app.seventime.se/api/2/customers/?limit=10&page=2" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/customers/?&limit=10&page=2";
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
    "totalResources": 33,
    "totalPages": 4,
    "currentPage": 2
  },
  "data": [
    {
      "_id": "571f61330c7f498a2d0001a4",
      "customerNumber": "733352",
      "vatNumber": "SE556596075301",
      "organizationNumber": "556596-0753",
      "email": "support@seventime.se",
      "phone": "0431-360050",
      "city": "Västra Karup",
      "zipCode": "269 74",
      "address": "Glimmingevägen 18",
      "name": "Tommy Hellström",
      "documents": [],
      "billingSettings": {
        "useSeparateBillingAddress": false,
        "address": "",
        "address2": "",
        "zipCode": "",
        "city": "",
        "useSeparateBillingEmail": false,
        "invoiceEmail": "",
        "invoiceDeliveryType": 0,
        "defaultEmailSubject": "",
        "isConstructionCompany": false,
        "isROTCustomer": true,
        "isRUTCustomer": false,
        "typeOfProperty": 1,
        "propertyDescription": "",
        "housingSocietyNumber": "",
        "apartmentNumber": "",
        "personalNumber": "",
        "deductionDistribution": [
          {
            "itemId": "0.40862768612862976",
            "userName": "Tommy Hellström",
            "personalNumber": "555555-5555",
            "distributionPercent": 100,
            "_id": "5bb2683d3a0fdb697e000080"
          }
        ],
        "expenseDiscount": 0,
        "expenseCustomProfitMargin": 0,
        "markupPercentSupplierInvoice": -1000,
        "priceList": null,
        "priceListName": ""
      },
      "modifiedDate": "2018-10-01T18:12:06.025Z",
      "createdDate": "2018-10-01T18:12:06.025Z",

      "address2": "",
      "country": "",
      "billingMethod": "",
      "pricePerHour": 0,
      "paymentDays": 20,
      "notes": "",
      "isActive": true
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves customers, a maximum of 500 customers will be returned.

### HTTP Request

`GET https://app.seventime.se/api/2/customers`

### Query Parameters

E.g. `https://app.seventime.se/api/2/customers/?organizationNumber=555555-5555`

Parameter | Default | Description
--------- | ------- | -----------
name                |  | If specified, customers that match the parameter will be included.
customerNumber      |    | If specified, customers that match the parameter will be included.
organizationNumber  |  | If specified, customers that match the parameter will be included.
city                |  | If specified, customers that match the parameter will be included.
sortBy              |  | If specified, a sort will be made on the specified parameter
sortDirection       |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


## Get a specific Customer

```shell
curl "https://app.seventime.se/api/2/customers/571f61330c7f498a2d0001a4" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/customers/571f61330c7f498a2d0001a4";
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
    "_id": "571f61330c7f498a2d0001a4",
    "customerNumber": "733352",
    "vatNumber": "SE556596075301",
    "organizationNumber": "556596-0753",
    "email": "support@seventime.se",
    "phone": "0431-360050",
    "city": "Västra Karup",
    "zipCode": "269 74",
    "address": "Glimmingevägen 18",
    "name": "Tommy Hellström",
    "documents": [],
    "billingSettings": {
      "useSeparateBillingAddress": false,
      "address": "",
      "address2": "",
      "zipCode": "",
      "city": "",
      "useSeparateBillingEmail": false,
      "invoiceEmail": "",
      "invoiceDeliveryType": 0,
      "defaultEmailSubject": "",
      "isConstructionCompany": false,
      "isROTCustomer": true,
      "isRUTCustomer": false,
      "typeOfProperty": 1,
      "propertyDescription": "",
      "housingSocietyNumber": "",
      "apartmentNumber": "",
      "personalNumber": "",
      "deductionDistribution": [
        {
          "itemId": "0.40862768612862976",
          "userName": "Tommy Hellström",
          "personalNumber": "555555-5555",
          "distributionPercent": 100,
          "_id": "5bb2683d3a0fdb697e000080"
        }
      ],
      "expenseDiscount": 0,
      "expenseCustomProfitMargin": 0,
      "markupPercentSupplierInvoice": -1000,
      "priceList": null,
      "priceListName": ""
    },
    "modifiedDate": "2018-10-01T18:12:06.025Z",
    "createdDate": "2018-10-01T18:12:06.025Z",
    "address2": "",
    "country": "",
    "billingMethod": "",
    "pricePerHour": 0,
    "paymentDays": 20,
    "notes": "",
    "isActive": true
  }
}
```

This endpoint retrieves a specific customer.



### HTTP Request

`GET https://app.seventime.se/api/2/customers/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the customer to retrieve


## Create a Customer
```shell
  curl -X POST "https://app.seventime.se/api/2/customers/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"createdByUser":"5f48eb3e65d7ee4942c46eeb","name":"Tommy Hellström","address":"Glimmingevägen 18","zipCode":"269 74","city":Västra Karup","phone":0431-360050","email":"support@seventime.se","organizationNumber":"555555-5555"}'
```

```javascript
let jsonData = {
  createdByUser: '5f48eb3e65d7ee4942c46eeb',
  name: 'Tommy Hellström',
  address: 'Glimmingevägen 18',
  zipCode: '269 74',
  city: 'Västra Karup',
  phone: '0431-360050',
  email: 'support@seventime.se',
  organizationNumber: '555555-5555'
};

let options = {
  url: 'https://app.seventime.se/api/2/customers',
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
    console.error("ERROR! Unable to create customer: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "_id": "571f61330c7f498a2d0001a4",
  "customerNumber": "733352",
  "organizationNumber": "555555-5555",
  "email": "support@seventime.se",
  "phone": "0431-360050",
  "city": "Västra Karup",
  "zipCode": "269 74",
  "address": "Glimmingevägen 18",
  "name": "Tommy Hellström",
  "documents": [],
  "billingSettings": {
    "deductionDistribution": []
  },
  "modifiedDate": "2018-10-01T18:12:06.025Z",
  "createdDate": "2018-10-01T18:12:06.025Z",
  "isActive": true
}
```

This endpoint creates a specific customer.

### HTTP Request

`POST https://app.seventime.se/api/2/customers/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
createdByUser       | String | Yes | Id of the user who created the customer
name                | String | Yes | Name of the customer
customerNumber      | String | No | Customer number. If specified it has to be unique otherwise an error will be returned. If not specified it will be set automatically.
address             | String | No | Address
address2            | String | No | Address 2
zipCode             | String | No | Zip code
city                | String | No | City
country             | String | No | Country code
phone               | String | No | Phone number
email               | String | No | Email address
organizationNumber  | String | No | Organization number or Personal number
vatNumber           | String | No | VAT number
paymentDays         | Number | No | Payment days for the user
deliveryAddress     | String | No | Contains attributes specific for delivery. See below for details.
billingSettings     | Object | No | Contains attributes specific for billing. See below for details.

**Attributes for deliveryAddress**

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
name                        | String | No | Name on delivery address
address                     | String | No | Primary delivery address
address2                    | String | No | Secondary delivery address
zipCode                     | String | No | Zip code
city                        | String | No | City
country                     | String | No | Country
phone                       | String | No | Phone number

**Attributes for billingSettings**

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
useSeparateBillingAddress   | Boolean | No | Should an alternative billing address be used?
address                     | String | No | Used if useSeparateBillingAddress is true
address2                    | String | No | Used if useSeparateBillingAddress is true
zipCode                     | String | No | Used if useSeparateBillingAddress is true
city                        | String | No | Used if useSeparateBillingAddress is true
useSeparateBillingEmail     | Boolean | No | If 'invoiceEmail' should be used
invoiceEmail                | String | No | Used for invoices if useSeparateBillingEmail is true
invoiceDeliveryType         | Number | No | Empty or 0 = Email, 10 = Postal letter, 20 = Svefaktura
defaultEmailSubject         | String | No | Default email subject for invoices
isConstructionCompany       | Boolean | No | Is construction company
isROTCustomer               | Boolean | No | Is ROT customer
isRUTCustomer               | Boolean | No | Is RUT customer
typeOfProperty              | Number | No | 1 = Detached property, 2 = Condominium
propertyDescription         | String | No | Swedish: Fastighetsbeteckning
housingSocietyNumber        | String | No | Swedish: Orgnr för bostadsrättsförening
apartmentNumber             | String | No | Swedish: Lägenhetsnummer
deductionDistribution       | Array | No | Array of DeductionItem's. See below for details.


**Attributes for DeductionItem**

DeductionItem is used to distribute ROT / RUT work

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
userName   | String| Yes | Full name of person
personalNumber   | String| Yes | Personal number
distributionPercent   | Number | Yes | 1-100

## Update a Customer

```shell
  curl -X PUT "https://app.seventime.se/api/2/customers/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"571f61330c7f498a2d0001a4","modifiedByUser":"5f48eb3e65d7ee4942c46eeb","name":"Seven Time AB","customerNumber":"733352"}' 
```

```javascript
let jsonData = {
  _id: '571f61330c7f498a2d0001a4',
  modifiedByUser: '5f48eb3e65d7ee4942c46eeb',
  name: 'Seven Time AB',
  customerNumber: '733352'
};

let options = {
  url: 'https://app.seventime.se/api/2/customers',
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
    console.log("Customer updated: " + body.name + ", _id: " + body._id);

  } else {
    console.error("ERROR! Unable to update customer: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "_id": "571f61330c7f498a2d0001a4",
  "customerNumber": "733352",
  "organizationNumber": "555555-5555",
  "email": "support@seventime.se",
  "phone": "0431-360050",
  "city": "Västra Karup",
  "zipCode": "269 74",
  "address": "Glimmingevägen 18",
  "name": "Seven Time AB",
  "documents": [],
  "billingSettings": {
    "deductionDistribution": []
  },
  "modifiedDate": "2018-10-01T18:12:06.025Z",
  "createdDate": "2018-10-01T18:12:06.025Z",
  "isActive": true  
}
"Customer updated: Seven Time AB, _id: 571f61330c7f498a2d0001a4"
```

This endpoint updates a specific customer.

### HTTP Request

`PUT https://app.seventime.se/api/2/customers/`

### PUT Parameters
The table below shows the required fields. Other available fields can be found in the section 'Create a Customer'.


Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                 | String | Yes | Id of the customer
modifiedByUser      | String | Yes | Id of the user who updated the customer

## Delete a Customer

```shell
  curl -X DELETE "https://app.seventime.se/api/2/customers/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"571f61330c7f498a2d0001a4","deletedByUser":"5f48eb3e65d7ee4942c46eeb"}' 
```

```javascript
let jsonData = {
  _id: '571f61330c7f498a2d0001a4',
  deletedByUser: 5f48eb3e65d7ee4942c46eeb
};

let options = {
  url: 'https://app.seventime.se/api/2/customers',
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
    console.log("Customer deleted: " + body.name + ", _id: " + body._id);

  } else {
    console.error("ERROR! Unable to delete customer: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "_id": "571f61330c7f498a2d0001a4",
  "customerNumber": "733352",
  "name": "Seven Time AB",
}
"Customer deleted: Seven Time AB, _id: 571f61330c7f498a2d0001a4"
```

This endpoint deletes a specific customer.

### HTTP Request

`DELETE https://app.seventime.se/api/2/customers/`

### DELETE Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                 | String | Yes | Id of the customer
deletedByUser       | String | Yes | Id of the user who deleted the customer


# Contact Persons

## Get Contact Persons


```shell
curl "https://app.seventime.se/api/2/contactPersons/?limit=2&page=4" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/contactPersons/?&limit=5&page=1";
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
    "totalResources": 3,
    "totalPages": 1,
    "currentPage": 1
  },
  "data": [
    {
      "_id": "5fb7bcd0ab7bb01d4d798762",
      "name": "Tommy",
      "title": "Utvecklare",
      "workPhone": "",
      "cellPhone": "",
      "email": "support@seventime.se",
      "customer": "5bb26376c42fb99275000080",
      "customerName": "Tommy Hellström",
      "mainContact": true,
      "isActive": true,
      "createdDate": "2020-11-17T12:06:24.281Z",
      "modifiedDate": "2020-11-17T12:06:24.281Z",
    },
    {
      // ...
    }
  ]
}

```

This endpoint retrieves contact persons, a maximum of 500 contact persons will be returned.

### HTTP Request

`GET https://app.seventime.se/api/2/contactPersons`

### Query Parameters

E.g. `https://app.seventime.se/api/2/contactPersons/?customerId=5bb26376c42fb99275000080`

Parameter | Default | Description
--------- | ------- | -----------
customerId      | | The id of the customer which the contact persons belong to. If not specified, all contact persons will be retrivied, regardless of which customer they belong to
sortBy          |  | If specified, a sort will be made on the specified parameter
sortDirection   |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get a specific Contact Person

```shell
curl "https://app.seventime.se/api/2/contactPersons/5fb7bcd0ab7bb01d4d798762" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/contactPersons/5fb7bcd0ab7bb01d4d798762";
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
    "_id": "5fb7bcd0ab7bb01d4d798762",
    "name": "Tommy",
    "title": "Utvecklare",
    "workPhone": "",
    "cellPhone": "",
    "email": "support@seventime.se",
    "customer": "5bb2775da1640a751f000082",
    "customerName": "Tommy Hellström",
    "mainContact": true,
    "isActive": true,
    "createdDate": "2020-11-17T12:06:24.281Z",
    "modifiedDate": "2020-11-17T12:06:24.281Z",
    "systemAccount": "5112826056d961c030000001",
  },
}
```

This endpoint retrieves a contact persons.

### HTTP Request

`GET https://app.seventime.se/api/2/contactPersons/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the contact person to retrieve

# Users
## Get Users

```shell
curl "https://app.seventime.se/api/2/users/?limit=10&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/users/?&limit=100&page=3";
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
    "totalResources": 4712,
    "totalPages": 48,
    "currentPage": 3
  },
  "data": [
    {
      "_id": "5f48eb3e65d7ee4942c4602",
      "firstName": "Tommy",
      "lastName": "Hellström",
      "email": "tommy@nummer7.se",
      "personalNumber": "",
      "employeeNumber": "",
      "userName": "20200828",
      "workPhone": "",
      "cellPhone": "",
      "createdDate": "2020-08-28T11:32:14.452Z",
      "modifiedDate": "2020-08-28T11:33:36.675Z",
      "userRoleId": 10,
      "isActive": true,
      "isActivated": true,
      "language": "SV"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves users, a maximum of 500 users will be returned.

### HTTP Request

`GET https://app.seventime.se/api/2/users`

### Query Parameters

E.g. `https://app.seventime.se/api/2/users/?name=Tommy Hellström`

Parameter | Default | Description
--------- | ------- | -----------
name              |  | If specified, users that match the parameter will be included.
personNumber      |  | If specified, users that match the parameter will be included.
department        |  | If specified, users that match the parameter will be included.
userRole          |  | If specified, users that match the parameter will be included.
isActive          |  | If specified, users that match the parameter will be included. This must be a boolean
isActivated       |  | If specified, users that match the parameter will be included. This must be a boolean
defaultSalaryType |  | If specified, users that match the parameter will be included.
userSkills        |  | If specified, users that match the parameter will be included.
sortBy            |  | If specified, a sort will be made on the specified parameter
sortDirection     |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


## Get a specific User

```shell
curl "https://app.seventime.se/api/2/users/59312765ad961c0318eb0a2" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/users/59312765ad961c0318eb0a2";
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
  "data":
  {
    "_id": "59312765ad961c0318eb0a2",
    "firstName": "Tommy",
    "lastName": "Hellström",
    "email": "tommy@nummer7.se",
    "personalNumber": "",
    "employeeNumber": "2",
    "userName": "tommy",
    "workPhone": "0431-360050",
    "cellPhone": "070-4580425",
    "createdDate": "2013-02-06T16:18:40.588Z",
    "modifiedDate": "2020-11-16T10:39:01.762Z",
    "userRoleId": 30,
    "isActive": true,
    "isActivated": true,
    "language": "EN"
  }
}
```

This endpoint retrieves a specific user



### HTTP Request

`GET https://app.seventime.se/api/2/users/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the user to retrieve

## Get User Roles

```shell
curl "https://app.seventime.se/api/2/userRoles/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/userRoles/";
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
      "userRoleId": 1,
      "userRoleName": "Administratör"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves user roles, a maximum of 500 user roles will be returned.



### HTTP Request

`GET https://app.seventime.se/api/2/userRoles/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get User Salary types

```shell
curl "https://app.seventime.se/api/2/defaultSalaryTypes/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/defaultSalaryTypes/";
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
      "_id": "5834419c7a27db6932000052",
      "name": "Övertid",
      "description": "",
      "code": "123",
      "isAbsenceTimeType": false,
      "isRuleType": false,
      "absenceTimeCategory": null,
      "absenceTimeCategoryName": "",
      "unitType": "1",
      "canBeRegistered": true,
      "salaryAmount": 0,
      "typeInSalarySystem": 10
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves user salary types, a maximum of 500 salary types will be returned.



### HTTP Request

`GET https://app.seventime.se/api/2/defaultSalaryTypes/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get User Skills

```shell
curl "https://app.seventime.se/api/2/userSkills/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/userSkills/";
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
      "_id": "59f9d1c53ffd5f932a000067",
      "skillTitle": "Höga arbeten",
      "requireEducations": [
        "5a54ea1f7a7fe3c26200006e"
      ]
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves user skills, a maximum of 500 user skills will be returned.

### HTTP Request

`GET https://app.seventime.se/api/2/userSkills/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get User Work Types

```shell
curl "https://app.seventime.se/api/2/userWorkTypes/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/userWorkTypes/";
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
      "_id": "5f442181e62efdb4a3a7d9c6d",
      "name": "Programmerare",
      "pricePerHour": 555,
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves user roles, a maximum of 500 user roles will be returned.


### HTTP Request

`GET https://app.seventime.se/api/2/userRoles/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Create a User

```shell
  curl -X POST "https://app.seventime.se/api/2/users/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"createdByUser":"5f48eb3e65d7ee4942c46eeb","firstName":"Tommy","lastName":"Hellström","email":"tommy@nummer7.se","userName":"TommyH","userRolesId":1"}'
```

```javascript
let jsonData = {
  createdByUser: '5f48eb3e65d7ee4942c46eeb',
  firstName: 'Tommy',
  lastName: 'Hellström',
  email: 'tommy@nummer7.se',
  userName: 'TommyH',
  userRoleId: 1,
};

let options = {
  url: 'https://app.seventime.se/api/2/users',
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
    console.error("ERROR! Unable to create user: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "_id": "5fb3e157f795553d05751946",
  "firstName": "Tommy",
  "lastName": "Hellström",
  "email": "tommy@nummer7.se",
  "personalNumber": "",
  "employeeNumber": "",
  "userName": "TommyH",
  "workPhone": "",
  "cellPhone": "",
  "createdDate": "2020-11-17T14:42:31.533Z",
  "modifiedDate": "2020-11-17T14:42:31.533Z",
  "userRoleId": 1,
  "isActive": false,
  "isActivated": false,
  "language": "SV"
}
```

This endpoint creates a user.

### HTTP Request

`POST https://app.seventime.se/api/2/users/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
firstName          | String   | Yes | First name of the user
lastName           | String   | Yes | Last name of the user
email              | String   | Yes | Email of the user
userName           | String   | Yes | Username
userRoleId         | String   | Yes | User role id
employeeNumber     | String   | No  | EmployeeNumber
workPhone          | String   | No  | Work phone number
cellPhone          | String   | No  | Cell phone number
isActive           | Boolean  | No  | Should the user be active?
isActivated        | Boolean  | No  | Should the user be activated?
password           | String   | No  | Password of the user
language           | String   | No  | Language of the user as a language code (e.g SV for Swedish). If not specified, this will we set to SV.

## Update a User

```shell
  curl -X PUT "https://app.seventime.se/api/2/users/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fb3e157f795553d05751946","modifiedByUser":"5f48eb3e65d7ee4942c46eeb","firstName":"Tommy","lastName":"Hellström","userName":"TommyH"}' 
```

```javascript
let jsonData = {
  _id: '5fb3e157f795553d05751946',
  modifiedByUser: '5f48eb3e65d7ee4942c46eeb',
  firstName: 'Tommy',
  lastName: 'Hellström',
  userName: 'TommyH'
};

let options = {
  url: 'https://app.seventime.se/api/2/users',
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
    console.log("User updated: " + body.firstName + ", _id: " + body._id);
  } else {
    console.error("ERROR! Unable to update user: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "_id": "5fb3e157f795553d05751946",
  "firstName": "Tommy",
  "lastName": "Hellström",
  "email": "tommy@nummer7.se",
  "userName": "TommyH",
  "createdDate": "2020-11-17T14:42:31.533Z",
  "modifiedDate": "2020-12-11T13:25:07.332Z",
  "userRoleId": 1,
  "isActive": true,
  "isActivated": false,
  "language": "SV"
}
"User updated: Tommy, _id: 5fb3e157f795553d05751946"
```

This endpoint updates a specific user.

### HTTP Request

`PUT https://app.seventime.se/api/2/users/`

### PUT Parameters

The table below shows the required fields. Other available fields can be found in the section 'Create a User'.

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                | String   | Yes | Id of the user
modifiedByUser     | String   | Yes | Id of the user who made the change

## Delete a User

```shell
  curl -X DELETE "https://app.seventime.se/api/2/users/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fb3e157f795553d05751946","deletedByUser":"5f48eb3e65d7ee4942c46eeb"}' 
```

```javascript
let jsonData = {
  _id: '5fb3e157f795553d05751946',
  deletedByUser: '5f48eb3e65d7ee4942c46eeb'
};

let options = {
  url: 'https://app.seventime.se/api/2/users',
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
    console.log("User deleted: " + body.firstName + ", _id: " + body._id);
  } else {
    console.error("ERROR! Unable to delete user: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "_id": "5fb3e157f795553d05751946",
  "firstName": "Tommy",
  "lastName": "Hellström",
}
"User deleted: Tommy, _id: 5fb3e157f795553d05751946"
```

This endpoint deletes a specific user.

### HTTP Request

`DELETE https://app.seventime.se/api/2/users/`

### DELETE Parameters


Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                | String   | Yes | Id of the user
deletedByUser      | String   | Yes | Id of the user who made the delete


# Departments

## Get Departments


```shell
curl "https://app.seventime.se/api/2/departments" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/departments/?";
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
    "totalResources": 3,
    "totalPages": 1,
    "currentPage": 1
  },
  "data": [
    {
      "_id": "59d05abdc471b72e4901079",
      "name": "Utveckling",
      "departmentNumber": "2",
      "isActive": true,
      "managerIds": [],
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves departments, a maximum of 500 departments will be returned.

### HTTP Request

`GET https://app.seventime.se/api/2/departments`

### Query Parameters

E.g. `https://app.seventime.se/api/2/departments/?`

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get a specific Department

```shell
curl "https://app.seventime.se/api/2/departments/59d05abdc471b72e4901079" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/departments/59d05abdc471b72e4901079";
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
    "managerIds": [],
    "_id": "59d05abdc471b72e4901079",
    "name": "Utveckling",
    "departmentNumber": "2",
    "isActive": true,
  }
}
```

This endpoint retrieves a specific department.



### HTTP Request

`GET https://app.seventime.se/api/2/departments/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the department to retrieve


# Projects

## Get Projects


```shell
curl "https://app.seventime.se/api/2/projects/?limit=10&page=7" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/projects/?&limit=10&page=7";
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
    "totalResources": 397,
    "totalPages": 40,
    "currentPage": 7
  },
  "data": [
    {
      "_id": "5f924f4f533f102af78f95b6",
      "permissions": {
        "permUsers": [],
        "permRoles": [],
        "permissionFlag": 1
      },
      "tags": [],
      "name": "Från offert 20200811",
      "projectNumber": "3314",
      "projectStatus": 50,
      "projectStatusRef": "5c8739d3205457b98b9883d4",
      "projectType": null,
      "projectTypeName": null,
      "billingMethod": "FIXED_PRICE",
      "pricePerHour": 0,
      "fixedPrice": 0,
      "fixedPriceInvoiced": false,
      "fixedPriceLeftToInvoice": 0,
      "fixedPriceExpenseItem": null,
      "timeCategoryPriceList": null,
      "estimatedTime": 0,
      "recurringBudgetType": 10,
      "recurringBudget": {
        "budgetTime": 0,
        "budgetAmount": 0,
        "budgetType": 10
      },
      "resultUnit": null,
      "resultUnitName": "",
      "customer": "5763e05bcddce98e3b00004b",
      "customerName": "Hellapps",
      "contactPerson": null,
      "contactPersonName": null,
      "projectLeader": null,
      "projectLeaderName": null,
      "quote": "5b110ea19b27f5ef3f00007b",
      "quoteNumber": "1058",
      "department": null,
      "departmentName": "",
      "marking": "",
      "yourOrderNumber": "1058",
      "deliveryAddress": {
        "name": "",
        "address": "",
        "address2": "",
        "zipCode": "",
        "city": "",
        "country": "",
        "phone": ""
      },
      "invoiceStatus": 0,
      "notes": "",
      "documents": [],
      "startDate": null,
      "endDate": null,
      "budget": {
        "typeOfBenefitCalc": 1,
        "benefits": [],
        "benefitTotal": 0,
        "typeOfCostCalc": 1,
        "costs": [],
        "costTotal": 0
      },
      "budgetCalculation": {
        "invoiceItems": [],
        "totalBenefitAmount": 0,
        "totalCostAmount": 0
      },
      "enableConstructionDiary": false,
      "enablePaymentPlans": false,
      "timeCategoryItems": [],
      "expenseItemItems": [],
      "staffLedger": {
        "workPlaceIDNumber": "",
        "developerName": "",
        "developerOrgNumber": ""
      },
      "projectTimeNotification": {
        "sent": false,
        "notifyAtPercent": 0
      },
      "workRuleStartOfDay": null,
      "workRuleEndOfDay": null,
      "timeLogRegistrationMethods": [],
      "timeShouldNotBeWorkTime": false,
      "enablePortalAccess": false,
      "projectResources": [],
      "checkLists": [],
      "color": "FAFAFA",
      "isActive": true,
      "comments": [],
      "customFields": [
        {
          "_id": "5f326f50433f102ff77f95d7",
          "fieldId": "5c0e7342ce9a647150000083",
          "value": "5c0e7342ce9a647150000085"
        }
      ],
      "createdDate": "2020-08-11T10:13:36.001Z",
      "modifiedDate": "2020-08-11T10:13:36.002Z",
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves projects, a maximum of 500 projects will be returned.

### HTTP Request

`GET https://app.seventime.se/api/2/projects`

### Query Parameters

E.g. `https://app.seventime.se/api/2/projects/?projectNumber=3314`

Parameter | Default | Description
--------- | ------- | -----------
name            |  | If specified, projects that match the parameter will be included.
projectNumber   |  | If specified, projects that match the parameter will be included.
sortBy          |  | If specified, a sort will be made on the specified parameter
sortDirection   |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending




## Get a specific project

```shell
curl "https://app.seventime.se/api/2/projects/5f924f4f533f102af78f95b6" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/projects/5f924f4f533f102af78f95b6";
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
    "recurringBudget": {
      "budgetTime": 0,
      "budgetAmount": 0,
      "budgetType": 10
    },
    "deliveryAddress": {
      "name": "",
      "address": "",
      "address2": "",
      "zipCode": "",
      "city": "",
      "country": "",
      "phone": ""
    },
    "budget": {
      "typeOfBenefitCalc": 1,
      "benefits": [],
      "benefitTotal": 0,
      "typeOfCostCalc": 1,
      "costs": [],
      "costTotal": 0
    },
    "budgetCalculation": {
      "invoiceItems": [],
      "totalBenefitAmount": 0,
      "totalCostAmount": 0
    },
    "permissions": {
      "permUsers": [],
      "permRoles": [],
      "permDepartments": [],
      "permissionFlag": 1
    },
    "staffLedger": {
      "workPlaceIDNumber": "",
      "developerName": "",
      "developerOrgNumber": ""
    },
    "projectTimeNotification": {
      "sent": false,
      "notifyAtPercent": 0
    },
    "tags": [],
    "_id": "5f326f4f433f102ff77f95d6",
    "name": "Från offert 20200811",
    "projectNumber": "3314",
    "projectStatus": 50,
    "projectStatusRef": "5c8639c3205457b88d9897b2",
    "projectType": null,
    "projectTypeName": null,
    "billingMethod": "FIXED_PRICE",
    "pricePerHour": 0,
    "fixedPrice": 0,
    "fixedPriceInvoiced": false,
    "fixedPriceLeftToInvoice": 0,
    "fixedPriceExpenseItem": null,
    "timeCategoryPriceList": null,
    "estimatedTime": 0,
    "recurringBudgetType": 10,
    "resultUnit": null,
    "resultUnitName": "",
    "customer": "5763e05bcddce98e3b00004b",
    "customerName": "Hellapps",
    "contactPerson": null,
    "contactPersonName": null,
    "projectLeader": null,
    "projectLeaderName": null,
    "quote": "5b110ea19b27f5ef3f00007b",
    "quoteNumber": "1058",
    "department": null,
    "departmentName": "",
    "marking": "",
    "yourOrderNumber": "1058",
    "invoiceStatus": 0,
    "notes": "",
    "documents": [],
    "startDate": null,
    "endDate": null,
    "enableConstructionDiary": false,
    "enablePaymentPlans": false,
    "timeCategoryItems": [],
    "expenseItemItems": [],
    "workRuleStartOfDay": null,
    "workRuleEndOfDay": null,
    "timeLogRegistrationMethods": [],
    "timeShouldNotBeWorkTime": false,
    "enablePortalAccess": false,
    "projectResources": [],
    "checkLists": [],
    "color": "FAFAFA",
    "isActive": true,
    "comments": [],
    "customFields": [
      {
        "_id": "5f326f50433f102ff77f95d7",
        "fieldId": "5c0e7342ce9a647150000083",
        "value": "5c0e7342ce9a647150000085"
      }
    ],
    "createdDate": "2020-08-11T10:13:36.001Z",
    "modifiedDate": "2020-08-11T10:13:36.002Z",
    "systemAccount": "5112826056d961c030000001",
  }
}
```

This endpoint retrieves a specific project.



### HTTP Request

`GET https://app.seventime.se/api/2/projects/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the project to retrieve

## Get Project statuses

```shell
curl "https://app.seventime.se/api/2/projectStatuses/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/projectStatuses/";
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
      "_id": "5c8639c4704957d88b9894b1",
      "statusName": "Avslutad",
      "color": "468847",
      "inProgressStatus": false,
      "closedStatus": true,
      "isActive": true
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves project statuses.



### HTTP Request

`GET https://app.seventime.se/api/2/projectStatuses/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get Project types

```shell
curl "https://app.seventime.se/api/2/projectTypes/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/projectTypes/";
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
      "_id": "5b276a908e0273b743607182",
      "projectTypeName": "Dev",
      "isActive": true,
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves project types.



### HTTP Request

`GET https://app.seventime.se/api/2/projectTypes/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get Project tags

```shell
curl "https://app.seventime.se/api/2/projectTags/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/projectTags/";
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
      "_id": "5fb2c736deb93b2713515684",
      "tagName": "Viktigt",
      "color": "673ab7"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves project tags.



### HTTP Request

`GET https://app.seventime.se/api/2/projectTags/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy        |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Create a Project
```shell
  curl -X POST "https://app.seventime.se/api/2/projects/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"createdByUser":"5f48eb3e65d7ee4942c46eeb","name":"App development"}' 
```

```javascript
const jsonData = {
  createdByUser: '5f48eb3e65d7ee4942c46eeb',
  name: 'App development',
};

const options = {
  url: 'https://app.seventime.se/api/2/projects',
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
    console.log("Project created: " + body.name + ", _id: " + body._id);
  } else {
    console.error("ERROR! Unable to create project: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
    "budget": { "benefits": [], "costs": [] },
    "budgetCalculation": { "invoiceItems": [] },
    "permissions": { "permUsers": [], "permRoles": [], "permDepartments": [] },
    "_id": "5fb3c92dd5472a243e9caa3b",
    "tags": [],
    "createdDate": "2020-11-17T12:59:25.109Z",
    "modifiedDate": "2020-11-17T12:59:25.109Z",
    "documents": [],
    "timeCategoryItems": [],
    "expenseItemItems": [],
    "timeLogRegistrationMethods": [],
    "projectResources": [],
    "checkLists": [],
    "comments": [],
    "customFields": [],
    "name": "App development",
    "projectNumber": "12345786" 
}
"Project created: App development, _id: 5fb3c92dd5472a243e9caa3b"
```

This endpoint creates a project.

### HTTP Request

`POST https://app.seventime.se/api/2/projects/name=App development`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
createdByUser           | String | Yes | Id of the user who created the project
name                    | String | Yes | Name of the project
projectNumber           | Number | No  | Project number must be unique if specified. If not specified, it will be automatically assigned
projectStatusRef        | String | No  | Id of the status of the project
customer                | String | No  | Id of the customer of the project
contactPerson           | String | No  | Id of the contact person. This field requires that customer is specified and that the customer person belongs to that customer
invoiceStatus           | Number | No  | Invoice status of the project. See below for available statuses
projectLeader           | String | No  | Id of the user who should be the project leader
projectType             | String | No  | Id of the project type
department              | String | No  | Id of the department
startDate               | String | No  | Start date of the project in the format YYYY-MM-DD
endDate                 | String | No  | End date of the project in the format YYYY-MM-DD
notes                   | String | No  | Notes to be included in the project
resultUnit              | String | No  | Id of the result unit of the project
billingMethod           | String | No  | Billing method of the project. See below for available billing methods
pricePerHour            | Number | No* | Required if billingMethod is set to HOURLY
fixedPrice              | Number | No* | Required if billingMethod is set to FIXED_PRICE
timeCategoryPriceList   | String | No* | Required if billingMethod is set to PRICELIST
projectTags             | Array  | No  | Array containing ids of tags
marking                 | String | No  | Marking on project
yourOrderNumber         | String | No  | Your order number
deliveryAddress         | Object | No  | Contains attributes for delivery address. See below for details


**Invoice statuses for projects**

Code | Status
--------- | ----------- 
0  | None
5  | Not invoiceable
10 | Ready to be invoiced
20 | Partly invoiced
30 | Fully invoiced

**Billing methods for projects**

Code | Billing method
--------- | ----------- 
ACCORDING_TO_CUSTOMER   | This requires that the customer has a billing method set
HOURLY                  | Hourly price
PERUSER                 | The price will be set per user
HOURLY_PER_TIMECATEGORY | Price will be set according to time category
FIXED_PRICE             | Fixed price
PRICELIST               | Price will be set according to a price list



**Attributes for deliveryAddress**

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
name                        | String | No | Name of delivery recipient
address                     | String | No | Primary address
address2                    | String | No | Secondary address
zipCode                     | String | No | Zip code
city                        | String | No | City
country                     | String | No | Country, given as a country code (E.g. SE for Sweden)
phone                       | String | No | Phone number

## Update a Project

```shell
  curl -X PUT "https://app.seventime.se/api/2/projects/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fb3c92dd5472a243e9caa3b","name":"App development","customer":"571f61330c7f498a2d0001a4"}' 
```

```javascript
const jsonData = {
  _id: '5fb3c92dd5472a243e9caa3b',
  modifiedByUser: '51718241fdb708f37959127',
  name: 'App development',
  customer: '571f61330c7f498a2d0001a4'
};

const options = {
  url: 'https://app.seventime.se/api/2/projects',
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
    console.log("Project updated: " + body.name + ", _id: " + body._id);
  } else {
    console.error("ERROR! Unable to update project: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
    "budget": { "benefits": [], "costs": [] },
    "budgetCalculation": { "invoiceItems": [] },
    "permissions": { "permUsers": [], "permRoles": [], "permDepartments": [] },
    "_id": "5fb3c92dd5472a243e9caa3b",
    "tags": [],
    "createdDate": "2020-11-17T12:59:25.109Z",
    "modifiedDate": "2020-11-17T12:59:25.109Z",
    "documents": [],
    "timeCategoryItems": [],
    "expenseItemItems": [],
    "timeLogRegistrationMethods": [],
    "projectResources": [],
    "checkLists": [],
    "comments": [],
    "customFields": [],
    "name": "App development",
    "projectNumber": "12345786",
    "customer": "571f61330c7f498a2d0001a4",
    "customerName": "Hellapps AB"
}
"Project updated: App development, _id: 5fb3c92dd5472a243e9caa3b"
```

This endpoint updates a project.

### HTTP Request

`PUT https://app.seventime.se/api/2/projects/name=App development&customer=571f61330c7f498a2d0001a4`

### PUT Parameters

The table below shows the required fields. Other available fields can be found in the section 'Create a Project'.

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                     | String | Yes | Id of the project
modifiedByUser          | String | Yes | Id of the user who made the change


## Delete a Project

```shell
  curl -X DELETE "https://app.seventime.se/api/2/projects/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fb3c92dd5472a243e9caa3b","deletedByUser":"51718241fdb708f379596193"}' 
```

```javascript
const jsonData = {
  _id: '5fb3c92dd5472a243e9caa3b',
  deletedByUser: '51718241fdb708f379596193'
};

const options = {
  url: 'https://app.seventime.se/api/2/projects',
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
    console.log("Project deleted: " + body.name + ", _id: " + body._id);
  } else {
    console.error("ERROR! Unable to delete project: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
    "_id": "5fb3c92dd5472a243e9caa3b",
    "name": "App development",
    "projectNumber": "12345786",
}
"Project deleted: App development, _id: 5fb3c92dd5472a243e9caa3b"
```

This endpoint deletes a project.

### HTTP Request

`DELETE https://app.seventime.se/api/2/projects/name=App development&customer=571f61330c7f498a2d0001a4`

### DELETE Parameters


Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                     | String | Yes | Id of the project
deletedByUser           | String | Yes | Id of the user who deleted the project


# Supplement Orders
## Get Supplement Orders

```shell
curl "https://app.seventime.se/api/2/supplementOrders/?project=5f924f4f533f102af78f95b6" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/supplementOrders/?&project=5f924f4f533f102af78f95b6";
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
    "totalResources": 1,
    "totalPages": 1,
    "currentPage": 1
  },
  "data": [
    {
      "_id": "5ba5619ad77ca8791257284",
      "title": "Discount",
      "description": "",
      "headerText": "",
      "supplementOrderNumber": 1,
      "supplementOrderType": 1,
      "createdByUser": "5f48eb3e65d7ee4942c46eeb",
      "createdByUserName": "Tommy Hellström",
      "customer": "5bb26376c42fb99275000080",
      "customerName": "Hellapps AB",
      "project": "5f924f4f533f102af78f95b6",
      "projectName": "Blåsippan",
      "projectNumber": "17058",
      "totalAmount": 75,
      "totalTaxAmount": 18.75,
      "totalAmountInclTax": 94,
      "taxPercent": 25,
      "contractedAmount": 0,
      "priceList": null,
      "priceListName": "",
      "billingMethod": "FIXED_PRICE",
      "acceptedDate": null,
      "acceptedWithSignature": false,
      "signaturePath": "",
      "deviation": null,
      "deviationNumber": 0,
      "publicLink": "B2R8LWK5bakDjEbdw7",
      "footerText": "<table width=\"100%\"><tr><td style='vertical-align: top;'></td><td style='vertical-align: top;'></td><td style='vertical-align: top;'></td></tr></table>",
      "deviations": [],
      "supplementOrderLogEntries": [
        {
          "logType": 1,
          "description": "",
          "user": "5f48eb3e65d7ee4942c46eeb",
          "userName": "Tommy Hellström",
          "_id": "5ba5619ad77ca8791257284",
          "logDate": "2018-09-25T07:12:46.369Z"
        },
        {
        // ...
        }
      ],
      "documents": [],
      "workOrderIds": [
        "5bae34dca878bd790d02065g"
      ],
      "invoiceIds": [
        "5f62c5281715836a4721b843",
        "524f29251c112373a3421613"
      ],
      "invoiceItems": [
        {
          "_id": null,
          "name": "",
          "description": "",
          "itemId": "0.9440031314948534",
          "itemOrder": 1024,
          "articleNumber": "203",
          "itemType": "expense",
          "timeCategory": null,
          "categoryName": "",
          "expenseItem": "5266af51d88751207100000e",
          "expenseItemName": "Seven Time - 5 användare - #2",
          "driverJournalItemType": null,
          "driverJournalItemTypeName": "",
          "machine": null,
          "machineName": "",
          "numberOfItems": 1,
          "unitPrice": 100,
          "priceList": null,
          "priceListName": null,
          "unit": "Styck",
          "unitCost": 0,
          "discountInPercent": 0,
          "supplementChargePercent": -25,
          "discountPercent": 0,
          "taxPercent": 25,
          "totalAmount": 75,
          "totalTaxAmount": 0,
          "totalAmountInclTax": 0,
          "totalCost": 0,
          "houseWorkFlag": false,
          "houseWorkTypeOfWork": 0,
          "selectedFlag": false,
          "createDate": null
        },
        {
        // ...
        }
      ],
      "modifiedDate": null,
      "createDate": "2018-09-25T07:12:46.369Z",
      "status": 60,
    }
  ]
}
```

This endpoint retrieves supplement orders, a maximum of 500 supplement orders will be returned.

### HTTP Request

`GET https://app.seventime.se/api/2/supplementOrders/?&project=5f924f4f533f102af78f95b6`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
projectId     |  | Id of the project that supplement orders will be retrieved from. This parameter is required
sortBy        |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get a specific Supplement Order

```shell
curl "https://app.seventime.se/api/2/supplementOrders/5ba5619ad77ca8791257284" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/supplementOrders/5ba5619ad77ca8791257284";
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
      "_id": "5ba5619ad77ca8791257284",
      "title": "Discount",
      "description": "",
      "headerText": "",
      "supplementOrderNumber": 1,
      "supplementOrderType": 1,
      "createdByUser": "5f48eb3e65d7ee4942c46eeb",
      "createdByUserName": "Tommy Hellström",
      "customer": "5bb26376c42fb99275000080",
      "customerName": "Hellapps AB",
      "project": "5f924f4f533f102af78f95b6",
      "projectName": "Blåsippan",
      "projectNumber": "17058",
      "totalAmount": 75,
      "totalTaxAmount": 18.75,
      "totalAmountInclTax": 94,
      "taxPercent": 25,
      "contractedAmount": 0,
      "priceList": null,
      "priceListName": "",
      "billingMethod": "FIXED_PRICE",
      "acceptedDate": null,
      "acceptedWithSignature": false,
      "signaturePath": "",
      "deviation": null,
      "deviationNumber": 0,
      "publicLink": "B2R8LWK5bakDjEbdw7",
      "footerText": "<table width=\"100%\"><tr><td style='vertical-align: top;'></td><td style='vertical-align: top;'></td><td style='vertical-align: top;'></td></tr></table>",
      "deviations": [],
      "supplementOrderLogEntries": [
        {
          "logType": 1,
          "description": "",
          "user": "5f48eb3e65d7ee4942c46eeb",
          "userName": "Tommy Hellström",
          "_id": "5ba5619ad77ca8791257284",
          "logDate": "2018-09-25T07:12:46.369Z"
        },
        {
        // ...
        }
      ],
      "documents": [],
      "workOrderIds": [
        "5bae34dca878bd790d02065g"
      ],
      "invoiceIds": [
        "5f62c5281715836a4721b843",
        "524f29251c112373a3421613"
      ],
      "invoiceItems": [
        {
          "_id": null,
          "name": "",
          "description": "",
          "itemId": "0.9440031314948534",
          "itemOrder": 1024,
          "articleNumber": "203",
          "itemType": "expense",
          "timeCategory": null,
          "categoryName": "",
          "expenseItem": "5266af51d88751207100000e",
          "expenseItemName": "Seven Time - 5 användare - #2",
          "driverJournalItemType": null,
          "driverJournalItemTypeName": "",
          "machine": null,
          "machineName": "",
          "numberOfItems": 1,
          "unitPrice": 100,
          "priceList": null,
          "priceListName": null,
          "unit": "Styck",
          "unitCost": 0,
          "discountInPercent": 0,
          "supplementChargePercent": -25,
          "discountPercent": 0,
          "taxPercent": 25,
          "totalAmount": 75,
          "totalTaxAmount": 0,
          "totalAmountInclTax": 0,
          "totalCost": 0,
          "houseWorkFlag": false,
          "houseWorkTypeOfWork": 0,
          "selectedFlag": false,
          "createDate": null
        },
        {
        // ...
        }
      ],
      "modifiedDate": null,
      "createDate": "2018-09-25T07:12:46.369Z",
      "status": 60,
   }
}
```

This endpoint retrieves a specific supplement order.

### HTTP Request

`GET https://app.seventime.se/api/2/supplementOrder/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the supplement order to retrieve

# Work Orders
## Get Work Orders

```shell
curl "https://app.seventime.se/api/2/workOrders/?limit=10&page=3" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/workOrders/?&limit=10&page3";
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
    "totalResources": 1772,
    "totalPages": 355,
    "currentPage": 34
  },
  "data": [
    {
      "_id": "5bae34dca878bd790d02065d",
      "workOrderNumber": 2901,
      "createdByUserName": "Tommy Hellström",
      "createdByUser": "59312765ad961c0318eb0a2",
      "statusRef": "587f3157c73c0f6d9cea944f",
      "status": 100,
      "customerNumber": "511",
      "customerName": "Abax Dörrsystem AB",
      "customer": "571f61330c7f498a2d0001a4",
      "estimatedTime": 0,
      "endDate": "2017-10-12T16:00:00.000Z",
      "startDate": "2017-10-10T07:00:00.000Z",
      "description": "",
      "title": "AO1",
      "customFields": [],
      "tags": [],
      "workOrderUserWorkTypes": [],
      "workOrderUserSkills": [],
      "budgetCalculation": {
        "invoiceItems": []
      },
      "invoiceRows": [],
      "todoItems": [],
      "reminders": [],
      "checkLists": [],
      "documents": [],
      "locationCoordinates": [],
      "workAddress": {
        "useOtherAddress": false,
        "address": "",
        "zipCode": "",
        "city": ""
      },
      "comments": [],
      "partTimeResources": [],
      "machines": [],
      "users": [],
      "createDate": "2018-09-28T13:17:16.785Z",
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves work orders, a maximum of 500 work orders will be returned.

### HTTP Request

`GET https://app.seventime.se/api/2/workOrders`

### Query Parameters

E.g. `https://app.seventime.se/api/2/workOrders/?workOrderNumber=5555`

Parameter | Default | Description
--------- | ------- | -----------
title           |  | If specified, work orders that match the parameter will be included.
workOrderNumber |  | If specified, work orders that match the parameter will be included.
project         |  | If specified, work orders that match the parameter will be included.
user            |  | If specified, work orders that match the parameter will be included.
customer        |  | If specified, work orders that match the parameter will be included.
sortBy          |  | If specified, a sort will be made on the specified parameter
sortDirection   |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending




## Get a specific Work order

```shell
curl "https://app.seventime.se/api/2/workOrders/5bae34dca878bd790d02065g" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/workOrders/5bae34dca878bd790d02065g";
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
    "workAddress": {
      "useOtherAddress": false,
      "address": "",
      "zipCode": "",
      "city": ""
    },
    "budgetCalculation": {
      "invoiceItems": []
    },
    "locationCoordinates": [],
    "tags": [],
    "_id": "5bae34dca878bd790d02065g",
    "workOrderNumber": 2901,
    "createdByUserName": "Tommy Hellström",
    "createdByUser": "59312765ad961c0318eb0a2",
    "systemAccount": "5112826056d961c030000001",
    "statusRef": "587f3157c73c0f6d9cea944f",
    "status": 100,
    "customerNumber": "511",
    "customerName": "Abax Dörrsystem AB",
    "customer": "571f61330c7f498a2d0001a4",
    "estimatedTime": 0,
    "endDate": "2017-10-12T16:00:00.000Z",
    "startDate": "2017-10-10T07:00:00.000Z",
    "description": "",
    "title": "AO1",
    "customFields": [],
    "workOrderUserWorkTypes": [],
    "workOrderUserSkills": [],
    "invoiceRows": [],
    "todoItems": [],
    "reminders": [],
    "checkLists": [],
    "documents": [],
    "comments": [],
    "partTimeResources": [],
    "machines": [],
    "users": [],
    "createDate": "2018-09-28T13:17:16.785Z",
    "relations": []
  }
}
```

This endpoint retrieves a specific work order.



### HTTP Request

`GET https://app.seventime.se/api/2/workOrders/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the work order to retrieve

## Get work order types

```shell
curl "https://app.seventime.se/api/2/workOrderTypes/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/workOrderTypes/";
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
      "_id": "58263d936a17605a25020043",
      "isActive": true,
      "workOrderTypeName": "Extra",
      "color": "f44336"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves work order types.



### HTTP Request

`GET https://app.seventime.se/api/2/workOrderTypes/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy          |  | If specified, a sort will be made on the specified parameter
sortDirection   |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get work order tags

```shell
curl "https://app.seventime.se/api/2/workOrderTags/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/workOrderTags/";
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
      "_id": "5df3a401f0690d1dbb3ec7bd",
      "tagName": "1",
      "color": "FAFAFA"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves work order tags.



### HTTP Request

`GET https://app.seventime.se/api/2/workOrderTags/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy        |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get Work order statuses

```shell
curl "https://app.seventime.se/api/2/workOrderStatuses/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/workOrderStatuses/";
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
      "_id": "582f7cabd16fdbe335041055",
      "statusName": "Ej planerad",
      "color": "FF5722",
      "inProgressStatus": false,
      "closedStatus": false,
      "isActive": true,
      "plannedStatus": false
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves work order statuses.



### HTTP Request

`GET https://app.seventime.se/api/2/workOrderStatuses/`

### URL Parameters

No parameters

## Create a Work order
```shell
  curl -X POST "https://app.seventime.se/api/2/workOrders/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"title":"Support","customer":"571f61330c7f498a2d0001a4","createdByUser":"5912626016d971c030916402"}' 
```

```javascript
let jsonData = {
  title: 'Support',
  customer: '571f61330c7f498a2d0001a4',
  createdByUser: '5912626016d971c030916402'
};

let options = {
  url: 'https://app.seventime.se/api/2/workOrders',
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
    console.error("ERROR! Unable to create work order: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
    "title": "Support"
    "workOrderNumber": 4908,       
    "description": "",   
    "locationCoordinates": [],
    "tags": [],
    "_id": "5fb8517e1bcaad1cd2cd3f9c",
    "createDate": "2020-11-16T10:15:42.216Z",
    "users": [],
    "machines": [],
    "partTimeResources": [],
    "comments": [],
    "documents": [],
    "checkLists": [],
    "reminders": [],
    "todoItems": [],
    "invoiceRows": [],
    "workOrderUserSkills": [],
    "workOrderUserWorkTypes": [],
    "customFields": [],
    "relations": [],
    "estimatedTime": 0, 
    "marking": "",
    "yourOrderNumber": "",
    "customerName": "Testbolaget ABC",
    "customer": "571f61330c7f498a2d0001a4",
    "color": "FF5722",
    "status": 500,
    "statusRef": "587f7dadd10fbbe338000055",
    "createdByUser":
    { 
    "_id": "5912626016d971c030916402"
    // ...
    },
    "createdByUserName": "Lucas Hellström",
}
```

This endpoint creates a work order.

### HTTP Request

`POST https://app.seventime.se/api/2/workOrders/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
title               | String | Yes | Title of the work order
customer            | String | Yes | Customer id for the customer who the work order should belong to
createdByUser       | String | Yes | Id of the user who created the work order
statusRef           | String | No | Id of the status of the work order.
Project             | String | No | Project id for the project which the work order should belong to
startDate           | String | No | Start date for the work order. The format must be YYYY-MM-DD HH:MM
endDate             | String | No | End date for the work order. The format must be YYYY-MM-DD HH:MM
currentOwner        | String | No | Id of the user who is the current owner of the work order
users               | Array  | No | Array containing the ids of users who are working full time on the work order
machines            | Array  | No | Array containing the ids of the machines which are working full time on the work order
estimatedTime       | Number | No | Estimated time required to finish the work order
contactPerson       | String | No | Id of the contact person
workOrderType       | String | No | Id of the work order type
department          | String | No | Id of the department
workLeader          | String | No | Id of the work leader
description         | String | No | Description of the work order
color               | String | No | Color of the work order, only used if "How to set color" is 'Manually' in settings. See below for available colors
invoiceStatus       | Number | No | Invoice status of the work order. See below for available statuses
billingMethod       | String | No | Billing method of work order. See below for available billing methods
fixedPrice          | Number | No* | *Only if Billing method is set to FIXED_PRICE
isSupplementOrder   | Boolean | No | Should the work order be set as supplement order?
workAddress         | Object | No | Contains attributes for work address. If not specified, the customers address will be set as work address. See below for details
enablePortalAccess  | Boolean | No | Should the work order be available in the customer portal?
allowRegistrationOfTimes     | Boolean | No | Should it be possible to register times on the work order?
allowRegistrationOfExpenses  | Boolean | No | Should it be possible to register expenses on the work order?
marking             | String | No | Marking on the work order
yourOrderNumber     | String | No | Your order number of the work order

**Colors for work orders**

<span style="width: 16px; height: 16px; background: #9c27b0;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 9c27b0 <br>
<span style="width: 16px; height: 16px; background: #673ab7;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 673ab7 <br>
<span style="width: 16px; height: 16px; background: #7C4DFF;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 7C4DFF <br>
<span style="width: 16px; height: 16px; background: #3F51B5;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 3F51B5 <br>
<span style="width: 16px; height: 16px; background: #3a87ad;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 3a87ad <br>

<span style="width: 16px; height: 16px; background: #2196F3;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 2196F3 <br>
<span style="width: 16px; height: 16px; background: #03A9F4;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 03A9F4 <br>
<span style="width: 16px; height: 16px; background: #00BCD4;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 00BCD4 <br>
<span style="width: 16px; height: 16px; background: #009688;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 009688 <br>
<span style="width: 16px; height: 16px; background: #468847;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 468847 <br>

<span style="width: 16px; height: 16px; background: #4CAF50;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 4CAF50 <br>
<span style="width: 16px; height: 16px; background: #8BC34A;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 8BC34A <br>
<span style="width: 16px; height: 16px; background: #CDDC39;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - CDDC39 <br>
<span style="width: 16px; height: 16px; background: #FF9800;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - FF9800 <br>
<span style="width: 16px; height: 16px; background: #FF5722;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - FF5722 <br>

<span style="width: 16px; height: 16px; background: #f44336;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - f44336 <br>
<span style="width: 16px; height: 16px; background: #e91e63;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - e91e63 <br>
<span style="width: 16px; height: 16px; background: #795548;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 795548 <br>
<span style="width: 16px; height: 16px; background: #5D4037;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 5D4037 <br>
<span style="width: 16px; height: 16px; background: #999999;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 999999 <br>

<span style="width: 16px; height: 16px; background: #666666;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 666666 <br>
<span style="width: 16px; height: 16px; background: #333333;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 333333 <br>
<span style="width: 16px; height: 16px; background: #000000;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 000000 <br>
<span style="width: 16px; height: 16px; background: #FAFAFA;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - FAFAFA <br>


**Invoice statuses for work orders**

Code | Status
--------- | ----------- 
0  | None
5  | Not invoiceable
10 | Ready to be invoiced
20 | Partly invoiced
30 | Fully invoiced

**Billing methods for work orders**

Code | Billing method
--------- | ----------- 
RUNNING             | Running price
FIXED_PRICE         | Fixed price
ACCORDING_TO_QUOTE  | Price will be set according to quote



**Attributes for workAddress**

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
useOtherAddress             | Boolean | Yes | Should an alternative work address be used?
name                        | String  | No  | Used if useSeparateBillingAddress is true
address                     | String  | No  | Used if useSeparateBillingAddress is true
address2                    | String  | No  | Used if useSeparateBillingAddress is true
zipCode                     | String  | No  | Used if useSeparateBillingAddress is true
city                        | String  | No  | Used if useSeparateBillingAddress is true
country                     | String  | No  | Used if useSeparateBillingAddress is true, given as a country code (E.g. SE for Sweden)
phone                       | String  | No  | Used if useSeparateBillingAddress is true

## Update a Work order


```shell
  curl -X PUT "https://app.seventime.se/api/2/workOrders/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fb8517e1bcaad1cd2cd3f9c","modifiedByUser":"5f48eb3e65d7ee4942c4602","title":"Construction work"}' 
```

```javascript
let jsonData = {
  _id: '5fb8517e1bcaad1cd2cd3f9c',
  modifiedByUser: '5f48eb3e65d7ee4942c4602',
  title: 'Construction work'
};

let options = {
  url: 'https://app.seventime.se/api/2/workOrders',
  json: jsonData,
  headers: {
    "Client-Secret": "thisismysecretkey",
    'Content-Type': 'application/json',
    'Accept': 'application/json'
  }
};

request.put(options, function (error, response, body) {
  if (!error && response.statusCode === 200) {
    console.log(body);
    console.log("Work Order updated: " + body.title + ", _id: " + body._id);
  } else {
    console.error("ERROR! Unable to update work order: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "runningInvoiceSettings":
   { 
     "oneRowText": "Arbetsorder #{{workOrderNumber}} {{workOrderTitle}}",
     "timeLogMachineSupplement": "nothing",
     "timeLogCustomField": "nothing",
     "includeDescription": true,
     "includeDateRange": false,
     "includeDate": true,
     "includeUser": true,
     "machineFromTimeLog": false,
     "includeCategory": true,
     "includeTask": false,
     "includeWorkOrder": false,
     "includeProject": false,
     "formatType": "detailedFormat" 
   },
  "budgetCalculation": { "invoiceItems": [] },
  "locationCoordinates": [],
  "tags": [],
  "_id": "5fb8517e1bcaad1cd2cd3f9c",
  "createDate": "2020-12-14T14:39:40.951Z",
  "users": [],
  "machines": [],
  "partTimeResources": [],
  "comments": [],
  "documents": [],
  "checkLists": [],
  "reminders":
   [ { "_id": "5321507b60913275921",
       "reminderTimeType": 4,
       "reminderTimeValue": 10,
       "reminderType": 1,
       "itemId": "0.2819101621862501" } ],
  "todoItems": [],
  "invoiceRows": [],
  "workOrderUserSkills": [],
  "workOrderUserWorkTypes": [],
  "customFields": [],
  "relations": [],
  "title": "Construction work",
  "estimatedTime": 0,
  "description": "",
  "marking": "",
  "yourOrderNumber": "",
  "customerName": "Hellapps",
  "customer": "571f61330c7f498a2d0001a4",
  "color": "FAFAFA",
  "status": 100,
  "statusRef": "582f7cabd16fdbe335041055",
  "createdByUser": "5f48eb3e65d7ee4942c4602",
  "createdByUserName": "Lucas Hellström",
  "workOrderNumber": 4942,
  "completedByUser": null,
  "completedByUserName": "",
  "completedDate": null,
  "inProgressByUser": null,
  "inProgressByUserName": "",
  "inProgressDate": null,
  "modifiedByUser": "5f48eb3e65d7ee4942c4602",
  "modifiedByUserName": "Lucas Hellström",
  "modifiedDate": "2020-12-14T14:43:29.158Z" 
}
"Work Order updated: Construction work, _id: 5fd7792cd6ec6e1f57bb8d8e"
```

This endpoint updates a work order.

### HTTP Request

`PUT https://app.seventime.se/api/2/workOrders/`

### PUT Parameters
The table below shows the required fields. Other available fields can be found in the section 'Create a Work Order'.

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id               | String | Yes | Id of the work order
modifiedByUser    | String | Yes | Id of the user who updated the work order

## Delete a Work order
```shell
  curl -X DELETE "https://app.seventime.se/api/2/workOrders" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"id":"5fb8517e1bcaad1cd2cd3f9c","deletedByUser":"5f48eb3e65d7ee4942c4602"}' 
```

```javascript
let jsonData = {
  _id: '5fb8517e1bcaad1cd2cd3f9c',
  deletedByUser: '5f48eb3e65d7ee4942c4602'
};

let options = {
  url: 'https://app.seventime.se/api/2/workOrders',
  json: jsonData,
  headers: {
    "Client-Secret": "thisismysecretkey",
    'Content-Type': 'application/json',
    'Accept': 'application/json'
  }
};

request.delete(options, function (error, response, body) {
  if (!error && response.statusCode === 200) {
    console.log(body);
    console.log("Work Order deleted: " + body.title + ", _id: " + body._id);
  } else {
    console.error("ERROR! Unable to delete work order: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "_id": "5fb8517e1bcaad1cd2cd3f9c",
  "title": "Construction work",
  "workOrderNumber": 4942,
}
"Work Order updated: Construction work, _id: 5fd7792cd6ec6e1f57bb8d8e"
```

This endpoint deletes a work order.

### HTTP Request

`DELETE https://app.seventime.se/api/2/workOrders/`

### DELETE Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id               | String | Yes | Id of the work order
deletedByUser    | String | Yes | Id of the user who deleted the work order

# Price lists

## Get price lists

```shell
curl "https://app.seventime.se/api/2/priceLists/?limit=10&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/priceLists/?&limit=10&page=1";
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
    "totalResources": 5,
    "totalPages": 1,
    "currentPage": 1
  },
  "data": [
    {
      "_id": "58c1504a658fb5911d018f5f",
      "name": "Grosslistan",
      "isActive": true,
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves price lists, a maximum of 500 price lists will be returned.

### HTTP Request

`GET https://app.seventime.se/api/2/priceLists`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


## Get a specific Price List

```shell
curl "https://app.seventime.se/api/2/priceLists/58c1504a658fb5911d018f5f" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/priceLists/58c1504a658fb5911d018f5f";
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
    "_id": "57bc187159a73f312300009d",
    "isActive": true,
    "systemAccount": "5112826056d961c030000001",
    "name": "ÅF-prislista",
  }
}
```

This endpoint retrieves a specific price list.


### HTTP Request

`GET https://app.seventime.se/api/2/priceLists/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the price list to retrieve

# Invoices

## Get Invoices


```shell
curl "https://app.seventime.se/api/2/invoices/?limit=3&page=9" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/invoices/?&limit=3&page=9";
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
    "totalResources": 1987,
    "totalPages": 663,
    "currentPage": 9
  },
  "data": [
    {
      "_id": "5fab29b038bd334ab540ab53",
      "deliveryAddress": {
        "name": "Kontoret",
        "address": "Glimmingevägen 18",
        "address2": "Testvägen 123",
        "zipCode": "12345",
        "city": "Västra Karup",
        "country": "SE",
        "phone": "12345-6798"
      },
      "houseProperties": {
        "typeOfProperty": 1,
        "propertyDescription": "property description test test",
        "housingSocietyNumber": "",
        "apartmentNumber": "",
        "maxDeductionAmount": 100000,
        "personalNumber": "",
        "deductionDistribution": [
          {
            "_id": "5fae99b072aa334cb539ab7d",
            "userName": "testUser",
            "personalNumber": "12345",
            "distributionPercent": 40
          },
          {
            // ...
          }
        ]
      },
      "workOrderIds": [
        "5fa2b550c289ea64821ea37b"
        // ...
      ],
      "tags": [
        "5f742440d608b2201c3e7bab",
        "5f74243ad608b2201c3e7ba9"
      ],
      "createDate": "2020-11-13T14:35:28.797Z",
      "invoiceItems": [
        {
          "_id": "5fae99b072aa334cb539ab7b",
          "createDate": "2020-11-13T14:35:28.795Z",
          "houseWorkTypeOfWork": 1,
          "name": "**Skivhantel i Gummi 10 Kg****",
          "description": "Skivhantel av järn",
          "expenseItem": "5de78ae9bb13565916362606",
          "expenseItemName": "**Skivhantel i Gummi 10 Kg****",
          "itemType": "expense",
          "numberOfItems": 1,
          "unit": "St",
          "unitCost": 319,
          "totalCost": 319,
          "discountPercent": 0,
          "taxPercent": 0,
          "unitPrice": 12345,
          "totalAmount": 12345,
          "totalTaxAmount": 0,
          "totalAmountInclTax": 12345,
          "itemId": "0.9281811863461673",
          "itemOrder": 1024,
          "houseWorkFlag": true
        },
        {
          // ...
        }
      ],
      "invoiceLogEntries": [
        {
          "_id": "5fae99b072aa334cb539ab7e",
          "logDate": "2020-11-13T14:35:28.797Z",
          "logType": 1,
          "description": "",
          "user": "51714655fbb708f379000003",
          "userName": "Lucas Hellström",
          "additionalData": ""
        },
        {
          // ...
        }
      ],
      "invoiceName": "Invoice",
      "marking": "marking test",
      "yourOrderNumber": "12345test test",
      "notes": "invoice notes test test test",
      "taxPercent": 12,
      "invoiceStatus": 2,
      "invoiceDate": "2020-11-04T23:00:00.000Z",
      "createdByUser": "51714655fbb708f379000003",
      "createdByUserName": "Lucas Hellström",
      "customer": "5cc05b6a4e595e684effc134",
      "customerName": "Hellapps AB",
      "dueDate": "2020-12-04T23:00:00.000Z",
      "language": "EN",
      "project": "5b20cce1d59a902e28000079",
      "projectName": "Blåsippan",
      "contactPerson": "5af95e6b1e56d1623800027d",
      "contactPersonName": "Bj�rn Romansoff",
      "ourReference": "518ff209d5af991b1c000003",
      "ourReferenceName": "Felix Hellström",
      "workOrder": "5fa2b550c289ea64821ea37b",
      "workOrderNumber": "4843",
      "invoiceType": 1,
      "resultUnit": "5784ff52fc71ce243d00004b",
      "resultUnitName": "Kontor Nord",
      "priceList": "57bc187159a73f312300009e",
      "priceListName": "Kundlista Inkl moms",
      "multipleTaxesOnRows": true,
      "currencyCode": "SEK",
      "totalAmount": 16549,
      "totalTaxAmount": 327.24,
      "totalAmountInclTax": 16876,
      "totalAmountRounding": -0.24,
      "sentDate": "2020-11-13T14:35:28.798Z",
      "invoiceNumber": "24481",
      "OCRNumber": "2448173",
      "archived": false,
      "archivedDate": null,
      "creditForInvoice": null,
      "creditForInvoiceNumber": "",
      "creditInvoice": null,
      "creditInvoiceNumber": "",
      "currencyRate": 1,
      "customerAddress": "Glimmingevägen 18<br>26974 Västra Karup",
      "customerEmail": "tommy@nummer7.se",
      "customerNumber": "3028",
      "customerOrgNo": "",
      "customerVAT": "",
      "description": null,
      "discountInPercent": 0,
      "exportedToEconomy": false,
      "footerInfoText": null,
      "footerText": "<table width=\"100%\"><tr><td style='vertical-align: top;'><div><div><span style=\"font-size: 11px;\">Test</span></div></div></td><td style='vertical-align: top;'><div><span style=\"font-size: 11px;\">Efter förfallodagen debiteras dröjsmålsränta: 13.0%</span></div><div><br></div></td><td style='vertical-align: top;'><span style=\"font-size: 11px;\">Äganderättsförbehåll tills full likvid erlagts</span><span style=\"font-size: 11px;\">.</span><br></td><td style='vertical-align: top;'><div><span style=\"font-size: 11px;\">Godkänd för F-skatt</span></div><div><br></div></td></tr></table>",
      "headerText": null,
      "houseDeductionAmount": 0,
      "houseDeductionBasisAmount": 0,
      "isCreditInvoice": false,
      "isCredited": false,
      "partiallyPaid": false,
      "paymentDate": null,
      "paymentPlan": null,
      "paymentPlanRowId": "",
      "quote": null,
      "quoteNumber": "",
      "reminderDate": null,
      "showPriceInclTaxesOnRows": false,
      "supplementOrder": null,
      "supplementOrderNumber": "",
      "totalCost": 4720
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves invoices, a maximum of 500 invoices will be returned.

### HTTP Request

`GET https://app.seventime.se/api/2/invoices`

### Query Parameters

E.g. `https://app.seventime.se/api/2/invoices/?invoiceNumber=24481`

Parameter | Default | Description
--------- | ------- | -----------
invoiceNumber       |  | If specified, invoices that match the parameter will be included.
OCRNumber           |  | If specified, invoices that match the parameter will be included.
customerNumber      |  | If specified, invoices that match the parameter will be included.
fromInvoiceDate     |  | If specified, invoices with invoice date after or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
toInvoiceDate       |  | If specified, invoices with invoice date before or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
fromDueDate         |  | If specified, invoices with due date after or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
toDueDate           |  | If specified, invoices with due date before or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
sortBy              |  | If specified, a sort will be made on the specified parameter
sortDirection       |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending




## Get a specific Invoice

```shell
curl "https://app.seventime.se/api/2/invoices/5fab29b038bd334ab540ab53" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/invoices/5fae99b072aa334cb539ab73";
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
    "deliveryAddress": {
      "name": "Kontoret",
      "address": "Glimmingevägen 18",
      "address2": "Testvägen 123",
      "zipCode": "12345",
      "city": "Västra Karup",
      "country": "SE",
      "phone": "12345-6798"
    },
    "houseProperties": {
      "typeOfProperty": 1,
      "propertyDescription": "property description test test",
      "housingSocietyNumber": "",
      "apartmentNumber": "",
      "maxDeductionAmount": 100000,
      "personalNumber": "",
      "deductionDistribution": [
        {
          "_id": "5fae99b072aa334cb539ab7d",
          "userName": "testUser",
          "personalNumber": "12345",
          "distributionPercent": 40
        },
        {
          // ...
        }
      ]
    },
    "timeLogIds": [],
    "expenseIds": [],
    "driverJournalIds": [],
    "machineTimeLogIds": [],
    "supplierInvoiceIds": [],
    "workOrderIds": [
      "5fa2b550c289ea64821ea37b"
    ],
    "externalSystemExport": [],
    "tags": [
      "5f742440d608b2201c3e7bab",
      "5f74243ad608b2201c3e7ba9"
    ],
    "_id": "5fae99b072aa334cb539ab73",
    "createDate": "2020-11-13T14:35:28.797Z",
    "invoiceItems": [
      {
        "createDate": "2020-11-13T14:35:28.795Z",
        "_id": "5fae99b072aa334cb539ab7b",
        "houseWorkTypeOfWork": 1,
        "name": "**Skivhantel i Gummi 10 Kg****",
        "description": "Skivhantel av järn",
        "expenseItem": "5de78ae9bb13565916362606",
        "expenseItemName": "**Skivhantel i Gummi 10 Kg****",
        "itemType": "expense",
        "numberOfItems": 1,
        "unit": "St",
        "unitCost": 319,
        "totalCost": 319,
        "discountPercent": 0,
        "taxPercent": 0,
        "unitPrice": 12345,
        "totalAmount": 12345,
        "totalTaxAmount": 0,
        "totalAmountInclTax": 12345,
        "itemId": "0.9281811863461673",
        "itemOrder": 1024,
        "houseWorkFlag": true
      },
      {
        // ...  
      }
    ],
    "documents": [],
    "invoiceLogEntries": [
      {
        "logDate": "2020-11-13T14:35:28.797Z",
        "_id": "5fae99b072aa334cb539ab7e",
        "logType": 1,
        "description": "",
        "user": "51714655fbb708f379000003",
        "userName": "Lucas Hellström",
        "additionalData": ""
      },
      {
        // ...
      }
    ],
    "partialPayments": [],
    "checkLists": [],
    "supplementOrders": [],
    "customFields": [
      {
        "_id": "5fb5217e4ea82f3df5febbcf",
        "fieldId": "5f67af2796bce73d3a61ff39",
        "value": {
          "distributorId": null,
          "distributorName": ""
        }
      }
    ],
    "invoiceName": "Invoice",
    "marking": "marking test",
    "yourOrderNumber": "12345test test",
    "notes": "invoice notes test test test",
    "taxPercent": 12,
    "invoiceStatus": 2,
    "invoiceDate": "2020-11-04T23:00:00.000Z",
    "createdByUser": "51714655fbb708f379000003",
    "createdByUserName": "Lucas Hellström",
    "customer": "5cc05b6a4e595e684effc134",
    "customerName": "Hellapps AB",
    "dueDate": "2020-12-04T23:00:00.000Z",
    "language": "EN",
    "project": "5b20cce1d59a902e28000079",
    "projectName": "Blåsippan",
    "contactPerson": "5af95e6b1e56d1623800027d",
    "contactPersonName": "Bj�rn Romansoff",
    "ourReference": "518ff209d5af991b1c000003",
    "ourReferenceName": "Felix Hellström",
    "workOrder": "5fa2b550c289ea64821ea37b",
    "workOrderNumber": "4843",
    "invoiceType": 1,
    "resultUnit": "5784ff52fc71ce243d00004b",
    "resultUnitName": "Kontor Nord",
    "priceList": "57bc187159a73f312300009e",
    "priceListName": "Kundlista Inkl moms",
    "multipleTaxesOnRows": true,
    "currencyCode": "SEK",
    "totalAmount": 16549,
    "totalTaxAmount": 327.24,
    "totalAmountInclTax": 16876,
    "totalAmountRounding": -0.24,
    "sentDate": "2020-11-13T14:35:28.798Z",
    "invoiceNumber": "24481",
    "OCRNumber": "2448173",
    "archived": false,
    "archivedDate": null,
    "creditForInvoice": null,
    "creditForInvoiceNumber": "",
    "creditInvoice": null,
    "creditInvoiceNumber": "",
    "currencyRate": 1,
    "customerAddress": "Glimmingevägen 18<br>26974 Västra Karup",
    "customerEmail": "tommy@nummer7.se",
    "customerNumber": "3028",
    "customerOrgNo": "",
    "customerVAT": "",
    "description": null,
    "discountInPercent": 0,
    "exportedToEconomy": false,
    "footerInfoText": null,
    "footerText": "<table width=\"100%\"><tr><td style='vertical-align: top;'><div><div><span style=\"font-size: 11px;\">Test</span></div></div></td><td style='vertical-align: top;'><div><span style=\"font-size: 11px;\">Efter förfallodagen debiteras dröjsmålsränta: 13.0%</span></div><div><br></div></td><td style='vertical-align: top;'><span style=\"font-size: 11px;\">Äganderättsförbehåll tills full likvid erlagts</span><span style=\"font-size: 11px;\">.</span><br></td><td style='vertical-align: top;'><div><span style=\"font-size: 11px;\">Godkänd för F-skatt</span></div><div><br></div></td></tr></table>",
    "headerText": null,
    "houseDeductionAmount": 0,
    "houseDeductionBasisAmount": 0,
    "isCreditInvoice": false,
    "isCredited": false,
    "partiallyPaid": false,
    "paymentDate": null,
    "paymentPlan": null,
    "paymentPlanRowId": "",
    "quote": null,
    "quoteNumber": "",
    "reminderDate": null,
    "showPriceInclTaxesOnRows": false,
    "supplementOrder": null,
    "supplementOrderNumber": "",
    "totalCost": 4720
  }
}
```

This endpoint retrieves a specific invoice.



### HTTP Request

`GET https://app.seventime.se/api/2/invoices/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the invoice to retrieve

## Get Invoice Tags

```shell
curl "https://app.seventime.se/api/2/invoiceTags/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/invoiceTags/";
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
      "_id": "5f742440d608b2201c3e7bab",
      "tagName": "Att granska",
      "color": "f44336"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves invoice tags.



### HTTP Request

`GET https://app.seventime.se/api/2/invoiceTags/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy          |  | If specified, a sort will be made on the specified parameter
sortDirection   |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Create an Invoice
```shell
  curl -X POST "https://app.seventime.se/api/2/invoices/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"invoiceStatus":"2","customer":"571f21058d7f618a2d037165","createdByUser":"51718241fdb708f37959127","language":"EN"}' 
```

```javascript
let jsonData = {
  invoiceStatus: 'Support',
  customer: '571f21058d7f618a2d037165',
  createdByUser: '51718241fdb708f37959127',
  language: 'EN'
};

let options = {
  url: 'https://app.seventime.se/api/2/invoices',
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
    console.log("Invoice created: _id: " + body._id);
  } else {
    console.error("ERROR! Unable to create invoice: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "timeLogIds": [],
  "expenseIds": [],
  "driverJournalIds": [],
  "machineTimeLogIds": [],
  "supplierInvoiceIds": [],
  "workOrderIds": [],
  "externalSystemExport": [],
  "tags": [],
  "_id": "5fb64449b0cc9510a561dfdf",
  "createDate": "2020-11-19T10:09:13.039Z",
  "invoiceItems": [],
  "documents": [],
  "invoiceLogEntries":
   [ 
    { "_id": "5fb64449b0cc9510a561dfe0",
       "logType": 1,
       "description": "",
       "user": "5f48eb3e65d7ee4942c4602",
       "userName": "Lucas Hellström",
       "additionalData": "",
       "logDate": "2020-11-19T10:09:13.039Z" },
     { 
     // ...
     } 
   ],
  "partialPayments": [],
  "checkLists": [],
  "supplementOrders": [],
  "customFields": [],
  "systemAccount": "5112826056d961c030000001",
  "invoiceName": "Invoice",
  "marking": "",
  "yourOrderNumber": "",
  "notes": "",
  "taxPercent": 25,
  "invoiceStatus": 2,
  "invoiceDate": "2020-11-19T10:09:13.033Z",
  "createdByUser": "5f48eb3e65d7ee4942c4602",
  "createdByUserName": "Lucas Hellström",
  "customer": "571f21058d7f618a2d037165",
  "customerName": "SevenTime",
  "dueDate": "2020-12-09T22":59":59.999Z",
  "language": "EN",
  "invoiceType": 0,
  "totalAmount": 0,
  "totalTaxAmount": 0,
  "totalAmountInclTax": 0,
  "totalAmountRounding": 0,
  "totalCost": 0,
  "sentDate": "2020-11-19T10:09:13.040Z",
  "invoiceNumber": "24511",
  "OCRNumber": "2451177",
}
"Invoice created: _id: 5fb64449b0cc9510a561dfdf"
```

This endpoint creates an invoice

### HTTP Request

`POST https://app.seventime.se/api/2/invoices/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
customer            | String | Yes | Customer id for the customer who the invoice should belong to
createdByUser       | String | Yes | Id of the user who created the invoice
language            | String | Yes | Language of the invoice given as a language code, e.g. SV for Swedish
name                | String | No | Name of the invoice. If not specified, this will be set to 'Invoice' translated to the selected language
invoiceDate         | String | No | Invoice date. Has to be in the format YYYY-MM-DD. If not specified, this will be set to the current date
dueDate             | String | No | Due date. Has to be in the format YYYY-MM-DD. If not specified, this will be set to the invoice date + the default payment terms
project             | String | No | Id of the project of the invoice
marking             | String | No | Marking on the invoice
yourOrderNumber     | String | No | Your order number
invoiceStatus       | Number | No | Status of the invoice. 1 for 'Draft' and 2 for 'Sent'
contactPerson       | String | No | Id of the contact person. This contact person has to belong to the selected customer
ourReference        | Number | No | Id of the user that will be set as our reference.
deliveryAddress     | Object | No | Contains attributes for delivery address. See below for details
workOrder           | String | No | Id of the work order
resultUnit          | String | No | Id of the result unit
invoiceType         | Number | No | Type of invoice. 0 for Normal, 1 for ROT, 2 for RUT and 3 for construction
houseProperties     | Object | No* | *Required if invoiceType is set to 1 or 2. See below for details
priceList           | String | No | Id of the price list to be used. If specified, prices from the price list will be used for invoice items
multipleTaxesOnRows | Boolean | No | Should it be possible to set different taxes on invoice items? If set to false, all invoice items will use the same tax percent
taxPercent          | Number | No | Tax percent which will be used if multipleTaxesOnRows is set to false. This must be 0, 6, 12 or 25% and if not specified will be set to 25%.
currencyCode        | String | No | Currency code to be used on the invoice
currencyRate        | Number | No | Currency rate between SEK and the selected currency
notes               | String | No | Notes on the invoice
invoiceItems        | Array  | No | Array containing objects with invoice items. See below for details.
tags                | Array  | No | Array of tag ids
useFooterFromSettings| Boolean | No | Do you want to use the footer that's specified in the settings?
footerText          | String | No | Footer text which will be used if useFooterFromSettings is set to false


**Attributes for deliveryAddress**

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
name                        | String | No | Name of delivery recipient
address                     | String | No | Primary address
address2                    | String | No | Secondary address
zipCode                     | String | No | Zip code
city                        | String | No | City
country                     | String | No | Country, given as a country code (E.g. SE for Sweden)
phone                       | String | No | Phone number

**House properties for ROT/RUT invoices**

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
typeOfProperty              | Number | Yes | Type of property. 1 for Detached property and 2 for Condominium association
propertyDescription         | String | No* | *Required if typeOfProperty is set to 1
housingSocietyNumber        | String | No* | *Required if typeOfProperty is set to 2
apartmentNumber             | String | No* | *Required if typeOfProperty is set to 2
deductionDistribution       | Array | No | Contains attributes for deduction distribution. See below for details

**Deduction distribution for ROT/RUT invoices**

The field deductionDistribution should be an array containing objects with the attributes shown below

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
userName              | Number | No | User name
personalNumber        | String | No | Personal number
distributionPercent   | String | No | Distribution percent


**Attributes for invoiceItems**

The field invoiceItems should be an array containing objects with the attributes shown below

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
itemType              | String | Yes | Item type of invoice row, see below for details
expenseItem           | String | No* | Id of the expense. *Required if itemType is expense
timeCategory          | String | No* | Id of the time category. *Required if itemType is timelog
machine               | String | No* | Id of the machine. *Required if itemType is machineTimeLog
driverJournalItemType | String | No* | Id of the driver journal. *Required if itemType is driverJournal
numberOfItems         | Number | No  | Quantity of the item. If not specified, this will be set to 1
unit                  | String | No  | Unit of the item
unitCost              | Number | No  | Purchase price of the item
unitPrice             | Number | No  | Unit price of the item
pricePerHour          | Number | No  | Price per hour. Used for time log rows
totalAmount           | Number | No  | Total amount. Used for onlyamount rows
discountPercent       | Number | No  | Discount of the item
taxPercent            | Number | No  | Tax percent of the item. Only used if multipleTaxesOnRows is true. This must be 0, 6, 12 or 25% and if not specified, this will be set to 25%.
houseWorkTypeOfWork   | Number | No  | Type of work for the row. Used if invoiceType is 1 or 2. See below for details

**Item types**

This table contains the different item types used in the field invoiceItems.itemTypes

Item type |  Description
--------- |-----------
expense        | Expense row
timeLog        | Time log row
general        | Free-text row
blank          | Blank row
text           | Text row
onlyamount     | Text+amount row
machineTimeLog | Machine time log row
driverJournal  | Driver journal row

**Available type of work for ROT/RUT invoices**

Code |  Invoice type | Description
--------- |----------- | -----------
0        |     | None
1        | ROT | Construction
2        | ROT | Electrical
3        | ROT | Windows/Metal
4        | ROT | Ground work
5        | ROT | Brick work
6        | ROT | Painting
7        | ROT | Plumbing
20       | ROT | Heat pump 30%
21       | ROT | Heat pump 35%
9        | RUT | Cleaning
10       | RUT | Textile
12       | RUT | Snow removal
13       | RUT | Gardening
14       | RUT | Child care
15       | RUT | Personal care
18       | RUT | Moving services
19       | RUT | IT services
22       | RUT | Repair of appliances

## Update an Invoice

```shell
  curl -X PUT "https://app.seventime.se/api/2/invoices/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fb64449b0cc9510a561dfdf","customer":"571f21058d7f618a2d037165","createdByUser":"51718241fdb708f37959127","language":"EN"}' 
```

```javascript
let jsonData = {
  _id: '5fb64449b0cc9510a561dfdf',
  modifiedByUser: '51718241fdb708f37959127',
  invoiceName: 'Invoice 2020-12',
  customer: '571f21058d7f618a2d037165',
  multipleTaxesOnRows: 'true',
  taxPercent: 25,
  invoiceItems: [{...}, ...]
};

let options = {
  url: 'https://app.seventime.se/api/2/invoices',
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
    console.log("Invoice updated: " + body.invoiceName + ", _id: " + body._id);
  } else {
    console.error("ERROR! Unable to update invoice: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "timeLogIds": [],
  "expenseIds": [],
  "driverJournalIds": [],
  "machineTimeLogIds": [],
  "supplierInvoiceIds": [],
  "workOrderIds": [],
  "externalSystemExport": [],
  "tags": [],
  "_id": "5fb64449b0cc9510a561dfdf",
  "createDate": "2020-11-19T10:09:13.039Z",
  "invoiceItems": [{...}, ...],
  "documents": [],
  "invoiceLogEntries":
   [ 
    { "_id": "5fb64449b0cc9510a561dfe0",
       "logType": 1,
       "description": "",
       "user": "5f48eb3e65d7ee4942c4602",
       "userName": "Lucas Hellström",
       "additionalData": "",
       "logDate": "2020-11-19T10:09:13.039Z" },
     { 
     // ...
     } 
   ],
  "partialPayments": [],
  "checkLists": [],
  "supplementOrders": [],
  "customFields": [],
  "systemAccount": "5112826056d961c030000001",
  "invoiceName": "Invoice 2020-12",
  "marking": "",
  "yourOrderNumber": "",
  "notes": "",
  "taxPercent": 25,
  "invoiceStatus": 2,
  "invoiceDate": "2020-11-19T10:09:13.033Z",
  "createdByUser": "5f48eb3e65d7ee4942c4602"
  "createdByUserName": "Lucas Hellström",
  "customer": "571f21058d7f618a2d037165",
  "customerName": "HellApps AB",
  "dueDate": "2020-12-09T22":59":59.999Z",
  "language": "EN",
  "invoiceType": 0,
  "totalAmount": 0,
  "totalTaxAmount": 0,
  "totalAmountInclTax": 0,
  "totalAmountRounding": 0,
  "totalCost": 0,
  "sentDate": "2020-11-19T10:09:13.040Z",
  "invoiceNumber": "24511",
  "OCRNumber": "2451177",
}
```

This endpoint updates an invoice

### HTTP Request

`PUT https://app.seventime.se/api/2/invoices/`

### PUT Parameters

The table below shows the required fields or fields that differ from 'Create an Invoice'. Other available fields can be found in the section 'Create an Invoice'.

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                     | String | Yes | Id of the invoice
modifiedByUser          | String | Yes | Id of the user who modified the invoice
multipleTaxesOnRows     | Boolean| Yes | Should it be possible to use different tax rates on invoice rows?
taxPercent              | Boolean| Yes*| Tax rate on invoice rows *Required if 'multipleTaxesOnRows' is false.
invoiceItems            | Array  | Yes | Array containing the invoice items. See the section 'Create an Invoice' for more information about these items
invoiceStatus           | Number | No  | Invoice status. 1 for 'Draft', 2 for 'Sent', 3 for 'Paid' and 4 for 'Obliterated'. Note that changing the status to 'Sent' will not send the invoice, this will mark the invoice as sent and give the invoice a number. It is only possible to set the status to 'Paid' or 'Obliterated' on a sent invoice.

## Delete an Invoice

```shell
  curl -X DELETE "https://app.seventime.se/api/2/invoices/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fb64449b0cc9510a561dfdf","deletedByUser":"51718241fdb708f37959127"}' 
```

```javascript
let jsonData = {
  _id: '5fb64449b0cc9510a561dfdf',
  deletedByUser: '51718241fdb708f37959127'
};

let options = {
  url: 'https://app.seventime.se/api/2/invoices',
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
    console.log("Invoice deleted: #" + body.invoiceNumber + ' ' + body.invoiceName);
  } else {
    console.error("ERROR! Unable to delete invoice: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "_id": "5fb64449b0cc9510a561dfdf",
  "invoiceName": "Invoice",
  "invoiceNumber": "24511",
}
"Invoice deleted: #24511 Invoice"
```

This endpoint deletes an invoice

### HTTP Request

`DELETE https://app.seventime.se/api/2/invoices/`

### DELETE Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id       | String | Yes | Id of the invoice
deletedByUser       | String | Yes | Id of the user who deleted the invoice


# Supplier invoices
## Get supplier invoices

```shell
curl "https://app.seventime.se/api/2/supplierInvoices/?limit=5&page=10" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/supplierInvoices/?&limit=5&page=10";
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
    "totalResources": 29,
    "totalPages": 10,
    "currentPage": 1
  },
  "data": [
    {
      "_id": "5f62c5281715836a4721b843",
      "isInvoiceable": false,
      "isInvoiced": false,
      "selfBillingTimeLogIds": [
        "5f5f6881241b6f02a6b20705",
        "5f5f6881241b6f02a6b2070b"
      ],
      "selfBillingExpenseIds": [
        "5f5f8c6a5b2317286eb838ab",
        "5f5f8c6a5b2317286eb838a8"
      ],
      "invoiceItems": [
        {
          "_id": "5f60c501271935b91231a941",
          "createDate": "2020-09-15T13:44:06.569Z",
          "articleNumber": "",
          "description": "Beredskap normal",
          "itemId": "0.949579694947744",
          "itemOrder": 1024,
          "unitCost": 550,
          "unitPrice": 550,
          "numberOfItems": 4,
          "totalAmount": 2200,
          "unit": "st",
          "taxPercent": 25,
          "totalAmountInclTax": 2750,
          "totalTaxAmount": 550,
          "totalCost": 2090,
          "itemType": "time",
          "timeCategory": "5e81d33db3f1cb30a8ef5514",
          "categoryName": "Beredskap normal"
        },
        {
          // ...
        }
      ],
      "documents": [],
      "distributor": "5f48eb7105b8ed6932c19eb9",
      "distributorName": "20200828",
      "yourReference": "Tommy Hellström",
      "createDate": "2020-09-15T13:44:06.566Z",
      "invoiceDate": "2020-09-15T13:44:06.566Z",
      "paymentDate": null,
      "totalAmount": 7681.7,
      "totalTaxAmount": 1920.425,
      "totalAmountInclTax": 9533.925,
      "taxPercent": 25,
      "taxType": 1,
      "markupPercent": 0,
      "currencyCode": "SEK",
      "currencyRate": 1,
      "OCR": "",
      "economySystemStatus": 0,
      "expensesCreatedFromInvoiceItems": false,
      "notes": "Självfaktura",
      "isCreditInvoice": false,
      "creditForInvoiceNumber": "",
      "isBooked": false,
      "economySystemRef": "",
      "importedFrom": "",
      "supplierInvoiceStatus": 5,
      "workOrder": "5f4df1793751c0916156ed5",
      "workOrderTitle": "Återkommande 20200116 - 234556565656",
      "workOrderNumber": 4737,
      "project": null,
      "projectName": null,
      "supplementOrderId": null,
      "supplementOrderNumber": null,
      "customer": "5bb26376c42fb99275000080",
      "customerName": "SevenTime",
      "department": null,
      "departmentName": "",
      "supplementOrder": false,
      "invoice": null,
      "invoiceNumber": "9316",
      "isSelfBillingInvoice": true,
      "selfBillingInvoiceStatus": 1,
      "exportedToEconomy": false,
      "selfBillingInvoice": "5f5f23fd7161761b55422c",
      "selfBillingInvoiceNumber": "24272",
      "footerText": "<table width=\"100%\"><tr><td style='vertical-align: top;'>Första</td><td style='vertical-align: top;'>Andra</td><td style='vertical-align: top;'>Tredje</td></tr></table>",
      "footerInfoText": "Text under...",
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves supplier invoices, a maximum of 500 supplier invoices will be returned.

### HTTP Request

`GET https://app.seventime.se/api/2/supplierInvoices`

### Query Parameters

E.g. `https://app.seventime.se/api/2/supplierInvoices/?supplierInvoiceNumber=9316`

Parameter | Default | Description
--------- | ------- | -----------
supplierInvoiceNumber    |  | If specified, supplier invoices that match the parameter will be included.
supplierInvoiceStatus    |  | If specified, supplier invoices that match the parameter will be included.
project                  |  | If specified, supplier invoices that match the parameter will be included.
customer                 |  | If specified, supplier invoices that match the parameter will be included.
workOrder           |  | If specified, supplier invoices that match the parameter will be included.
workOrderNumber          |  | If specified, supplier invoices that match the parameter will be included.
distributor              |  | If specified, supplier invoices that match the parameter will be included.
fromInvoiceDate          |  | If specified, supplier invoices that match the parameter will be included.
toInvoiceDate            |  | If specified, supplier invoices that match the parameter will be included.
isInvoiceable            |  | If specified, supplier invoices that match the parameter will be included.
sortBy                   |  | If specified, a sort will be made on the specified parameter
sortDirection            |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending



## Get a specific Supplier Invoice

```shell
curl "https://app.seventime.se/api/2/supplierInvoices/5f62c5281715836a4721b843" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/supplierInvoices/5f62c5281715836a4721b843";
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
    "_id": "5f62c5281715836a4721b843",
    "isInvoiceable": false,
    "isInvoiced": false,
    "selfBillingTimeLogIds": [
      "5f5f6881241b6f02a6b20705",
      "5f5f6881241b6f02a6b2070b"
    ],
    "selfBillingExpenseIds": [
      "5f5f8c6a5b2317286eb838ab",
      "5f5f8c6a5b2317286eb838a8"
    ],
    "invoiceItems": [
      {
        "_id": "5f60c501271935b91231a941",
        "createDate": "2020-09-15T13:44:06.569Z",
        "articleNumber": "",
        "description": "Beredskap normal",
        "itemId": "0.949579694947744",
        "itemOrder": 1024,
        "unitCost": 550,
        "unitPrice": 550,
        "numberOfItems": 4,
        "totalAmount": 2200,
        "unit": "st",
        "taxPercent": 25,
        "totalAmountInclTax": 2750,
        "totalTaxAmount": 550,
        "totalCost": 2090,
        "itemType": "time",
        "timeCategory": "5e81d33db3f1cb30a8ef5514",
        "categoryName": "Beredskap normal"
      },
      {
        // ...
      }
    ],
    "documents": [],
    "distributor": "5f48eb7105b8ed6932c19eb9",
    "distributorName": "20200828",
    "yourReference": "Tommy Hellström",
    "createDate": "2020-09-15T13:44:06.566Z",
    "invoiceDate": "2020-09-15T13:44:06.566Z",
    "paymentDate": null,
    "totalAmount": 7681.7,
    "totalTaxAmount": 1920.425,
    "totalAmountInclTax": 9533.925,
    "taxPercent": 25,
    "taxType": 1,
    "markupPercent": 0,
    "currencyCode": "SEK",
    "currencyRate": 1,
    "OCR": "",
    "economySystemStatus": 0,
    "expensesCreatedFromInvoiceItems": false,
    "notes": "Självfaktura",
    "isCreditInvoice": false,
    "creditForInvoiceNumber": "",
    "isBooked": false,
    "economySystemRef": "",
    "importedFrom": "",
    "supplierInvoiceStatus": 5,
    "workOrder": "5f4df1793751c0916156ed5",
    "workOrderTitle": "Återkommande 20200116 - 234556565656",
    "workOrderNumber": 4737,
    "project": null,
    "projectName": null,
    "supplementOrderId": null,
    "supplementOrderNumber": null,
    "customer": "5bb26376c42fb99275000080",
    "customerName": "SevenTime",
    "department": null,
    "departmentName": "",
    "supplementOrder": false,
    "invoice": null,
    "invoiceNumber": "9316",
    "isSelfBillingInvoice": true,
    "selfBillingInvoiceStatus": 1,
    "exportedToEconomy": false,
    "selfBillingInvoice": "5f5f23fd7161761b55422c",
    "selfBillingInvoiceNumber": "24272",
    "footerText": "<table width=\"100%\"><tr><td style='vertical-align: top;'>Första</td><td style='vertical-align: top;'>Andra</td><td style='vertical-align: top;'>Tredje</td></tr></table>",
    "footerInfoText": "Text under...",
  }
}
```

This endpoint retrieves a specific supplier invoice.



### HTTP Request

`GET https://app.seventime.se/api/2/supplierInvoices/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the supplier invoice to retrieve

## Create a Supplier Invoice

```shell
  curl -X POST "https://app.seventime.se/api/2/supplierInvoices/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"supplierInvoiceNumber":"9162","createdByUser":"5f48eb3e65d7ee4942c46eeb","distributor":"5f6b2e6af24d5df55b69277","totalAmountInclTax":"100000"}' 
```

```javascript
let jsonData = {
  supplierInvoiceNumber: 9162,
  createdByUser: '5f48eb3e65d7ee4942c46eeb',
  distributor: '5f6b2e6af24d5df55b69277',
  totalAmountInclTax: 100000
};

let options = {
  url: 'https://app.seventime.se/api/2/supplierInvoices',
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
    console.error("ERROR! Unable to create supplier invoice: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "isInvoiceable": true,
  "selfBillingTimeLogIds": [],
  "selfBillingExpenseIds": [],
  "_id": "5fd0619c7391b561bda0a7",
  "invoiceItems": [],
  "documents": [],
  "supplierInvoiceLogEntries": [ 
    { 
      "_id": "5fdd142c621b21a10129",
      "logType": 1,
      "description": "",
      "user": "5f48eb3e65d7ee4942c46eeb",
      "userName": "Tommy Hellström",
      "logDate": "2020-12-09T12":43":51.516Z" 
    } 
  ],
  "markupPercent": 0,
  "distributor": "5f6b2e6af24d5df55b69277",
  "distributorName": "Hellapps AB",
  "supplierInvoiceNumber": "9162",
  "invoiceDate": "2020-12-09T12:43:51.515Z",
  "dueDate": "2020-12-09T12:43:51.515Z",
  "totalAmountInclTax": 100000,
  "taxPercent": 25,
  "totalAmount": 80000,
  "totalTaxAmount": 20000,
  "totalAmountToInvoice": 80000,
  "supplierInvoiceStatus": 1,
  "createDate": "2020-12-09T12:43:51.515Z",
}
```

This endpoint creates a supplier invoice

### HTTP Request

`POST https://app.seventime.se/api/2/supplierInvoices/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
supplierInvoiceNumber     | Number | Yes | Number of  the supplier invoice
createdByUser             | String | Yes | Id of the user who created the supplier invoice
distributor               | String | Yes | Id of the distributor
totalAmountInclTax        | Number | Yes | Total amount incl. tax on the supplier invoice
customer                  | String | No | Id of the customer
project                   | String | No | Id of the project
workOrder                 | String | No | Id of the work order. The work order must belong to the specified project
resultUnit                | String | No | Id of the result unit
supplierInvoiceStatus     | Number | No | Status of the supplier invoice. 1 for 'Registered', 5 for 'Draft', 7 for 'Sent' and 10 for 'Invoiced'
taxPercent                | Number | No | Tax on the supplier invoice as a percentage. Ex: 25 for 25% tax
markupPercent             | Number | No | Markup on the supplier invoice as a percentage. Ex: 10 for 10% markup
invoiceDate               | String | No | Invoice date in the format 'YYYY-MM-DD'
dueDate                   | String | No | Due date in the format 'YYYY-MM-DD'
exportedToEconomy         | Boolean| No | Is the supplier invoice exported to a economy system?
OCR                       | Number | No | OCR number of the invoice
currencyCode              | String | No | Currency code to be used on the supplier invoice
currencyRate              | Number | No*| Currency rate between SEK and the selected currency. *Required if currencyCode is not 'SEK'. This will always be set to 1 if currencyCode is 'SEK'
supplementOrder           | Boolean| No | Should the supplier invoice be a supplement order? This is only available if the project or work order is set to use a fixed price
supplementOrderId         | String | No | Id of the supplement order
ourReference              | String | No | Our reference
yourReference             | String | No | Your reference
notes                     | String | No | Notes on the supplier invoice
isInvoiceable             | Boolean| No | Is the supplier invoice invoiceable?
invoiceItems              | Array  | No | Array containing objects with invoice items. See below for details.

**Attributes for invoiceItems**

The field invoiceItems should be an array containing objects with the attributes shown below

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
itemType              | String | Yes | Item type of invoice row, see below for details
expenseItem           | String | No* | Id of the expense. *Required if itemType is expense
timeCategory          | String | No* | Id of the time category. *Required if itemType is timelog
machine               | String | No* | Id of the machine. *Required if itemType is machineTimeLog
driverJournalItemType | String | No* | Id of the driver journal. *Required if itemType is driverJournal
numberOfItems         | Number | No  | Quantity of the item. If not specified, this will be set to 1
unit                  | String | No  | Unit of the item
unitCost              | Number | No  | Purchase price of the item
unitPrice             | Number | No  | Unit price of the item
pricePerHour          | Number | No  | Price per hour. Used for time log rows
totalAmount           | Number | No  | Total amount. Used for onlyamount rows
discountPercent       | Number | No  | Discount of the item

**Item types**

This table contains the different item types used in the field invoiceItems.itemTypes

Item type |  Description
--------- |-----------
expense        | Expense row
timeLog        | Time log row
general        | Free-text row
blank          | Blank row
text           | Text row
onlyamount     | Text+amount row
machineTimeLog | Machine time log row
driverJournal  | Driver journal row

## Update a Supplier Invoice

```shell
  curl -X POST "https://app.seventime.se/api/2/supplierInvoices/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fd0619c7391b561bda0a7","modifiedByUser":"5f48eb3e65d7ee4942c46eeb","supplierInvoiceStatus":"7"}' 
```

```javascript
let jsonData = {
  _id: "5fd0619c7391b561bda0a7",
  modifiedByUser: '5f48eb3e65d7ee4942c46eeb',
  supplierInvoiceStatus: 10
};

let options = {
  url: 'https://app.seventime.se/api/2/supplierInvoices',
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
    console.log("Supplier invoice updated: _id: " + body._id);

  } else {
    console.error("ERROR! Unable to update supplier invoice: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "isInvoiceable": true,
  "selfBillingTimeLogIds": [],
  "selfBillingExpenseIds": [],
  "_id": "5fd0619c7391b561bda0a7",
  "invoiceItems": [],
  "documents": [],
  "supplierInvoiceLogEntries": [ 
    { 
      "_id": "5fdd142c621b21a10129",
      "logType": 1,
      "description": "",
      "user": "5f48eb3e65d7ee4942c46eeb",
      "userName": "Tommy Hellström",
      "logDate": "2020-12-09T12":43":51.516Z" 
    } 
  ],
  "markupPercent": 0,
  "distributor": "5f6b2e6af24d5df55b69277",
  "distributorName": "Hellapps AB",
  "supplierInvoiceNumber": "9162",
  "invoiceDate": "2020-12-09T12:43:51.515Z",
  "dueDate": "2020-12-09T12:43:51.515Z",
  "totalAmountInclTax": 100000,
  "taxPercent": 25,
  "totalAmount": 80000,
  "totalTaxAmount": 20000,
  "totalAmountToInvoice": 80000,
  "supplierInvoiceStatus": 10,
  "createDate": "2020-12-09T12:43:51.515Z",
}
"Supplier invoice updated: _id: 5fd0619c7391b561bda0a7"
```

This endpoint updates a supplier invoice

### HTTP Request

`PUT https://app.seventime.se/api/2/supplierInvoices/`

### PUT Parameters
The table below shows the required fields. Other available fields can be found in the section 'Create an Invoice'.


Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                 | String      | Yes | Id of the Supplier Invoice
modifiedByUser      | String      | Yes | Id of the user who made the change

## Delete a Supplier Invoice

```shell
  curl -X DELETE "https://app.seventime.se/api/2/supplierInvoices/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fd0619c7391b561bda0a7"}' 
```

```javascript
let jsonData = {
  _id: "5fd0619c7391b561bda0a7"
};

let options = {
  url: 'https://app.seventime.se/api/2/supplierInvoices',
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
    console.log("Supplier invoice updated: _id: " + body._id + ', number: ' + body.supplierInvoiceNumber);

  } else {
    console.error("ERROR! Unable to delete supplier invoice: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "_id": "5fd0619c7391b561bda0a7",
  "supplierInvoiceNumber": "9162",
}
"Supplier invoice deleted: _id: 5fd0619c7391b561bda0a7, number: 9162"
```

This endpoint deletes a supplier invoice

### HTTP Request

`DELETE https://app.seventime.se/api/2/supplierInvoices/`

### DELETE Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                 | String      | Yes | Id of the Supplier Invoice

# Machines
## Get Machines


```shell
curl "https://app.seventime.se/api/2/machines/?limit=10&page=2" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/machines/?&limit=10&page=2";
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
      "_id": "5a4bc02e40a13d7179005920",
      "lastHoursUsedRegDate": "2020-09-27T12:06:19.225Z",
      "hoursUsed": 5193,
      "lastMileageRegDate": "2020-09-27T12:06:19.225Z",
      "mileage": 10122.7,
      "isActive": true,
      "createdByUserName": "Tommy Hellström",
      "createdByUser": "5113986056b831a915810002",
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

This endpoint retrieves machines, a maximum of 500 machines will be returned.

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
    "trackunitData": {
      "id": "1135803"
    },
    "machineLog": [],
    "isSupplementForMachines": [],
    "_id": "5a4bc02e40a13d7179005920",
    "lastHoursUsedRegDate": "2020-09-27T12:06:19.225Z",
    "hoursUsed": 5193,
    "lastMileageRegDate": "2020-09-27T12:06:19.225Z",
    "mileage": 10122.7,
    "isActive": true,
    "systemAccount": "5112826056d961c030000001",
    "createdByUserName": "Tommy Hellström",
    "createdByUser": "5113986056b831a915810002",
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
      "_id": "57e89fbae191f8ba2b28420",
      "name": "Fordon",
      "isActive": true,
      "createDate": "2017-10-19T12:50:50.361Z",
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


# Machine Time Logs

## Get Machine Time Logs

```shell
curl "https://app.seventime.se/api/2/machineTimeLogs/?limit=2&page=27" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/machineTimeLogs/?&limit=2&page=27";
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

This endpoint retrieves machine time logs, a maximum of 500 machine time logs will be returned.

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

# Time Logs
## Get Time Logs


```shell
curl "https://app.seventime.se/api/2/timeLogs/?limit=3&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/timeLogs/?&limit=3&page=1";
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
      "_id": "514959f8733259db7591000c",
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
      "user": "51203146506d961c030791801",
      "userName": "Tommy Hellström",
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
          "_id": "5f57385dbe6f05476e59e603",
          "salaryType": "58cb7f24e9c363d0b0a06298a",
          "salaryTypeName": "OB kväll",
          "costPerHour": 150,
          "time": 6
        },
        {
          "_id": "5f57385dbe6f05476e59e816",
          "salaryType": "58cb7f24e9c363d0b0a06298a",
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

This endpoint retrieves machines time logs, a maximum of 500 machine time logs will be returned.

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
timestamp          |  | If specified, time logs that start after the given date and time will be included. The date has to be in the format 'YYYY-MM-HH HH:MM'
endTimestamp       |  | If specified, time logs that end before the given date and time will be included. The date has to be in the format 'YYYY-MM-HH HH:MM'
sortBy             |  | If specified, a sort will be made on the specified parameter
sortDirection      |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending





## Get a specific Time Log

```shell
curl "https://app.seventime.se/api/2/timeLogs/514959f8733259db7591000c" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/timeLogs/514959f8733259db7591000c";
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
    "_id": "514959f8733259db7591000c",
    "cost": 10690.5824,
    "createDate": "2013-03-16T11:39:36.437Z",
    "customer": null,
    "description": "",
    "endTimestamp": "2013-03-16T11:39:35.000Z",
    "isWorkTime": true,
    "project": null,
    "time": 41.18577972222222,
    "timeCategory": null,
    "timestamp": "2013-03-14T18:28:26.193Z",
    "user": "51203146506d961c030791801",
    "userName": "Tommy Hellström",
    "invoiceableTime": 41.18577972222222,
    "customFields": [],
    "machineTimePrices": [],
    "machineTimeSupplements": [],
    "realTimestamp": "2020-08-27T07:52:57.685Z",
    "unSocialHoursCosts": [
      {
        "_id": "5f57385dbe6f05476e59e603",
        "salaryType": "58cb7f24e9c363d0b0a06298a",
        "salaryTypeName": "OB kväll",
        "costPerHour": 150,
        "time": 6
      },
      {
        "_id": "5f57385dbe6f05476e59e816",
        "salaryType": "58cb8f2e9c663d0e0a00005a",
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
      "_id": "58cd3c4771b8a3c347041207",
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
curl "https://app.seventime.se/api/2/timeCategories/58cd3c4771b8a3c347041207" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/timeCategories/58cd3c4771b8a3c347041207";
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
    "_id": "58cd3c4771b8a3c347041207",
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
  -d '{"createdByUser":"5f48eb3e65d7ee4942c46eeb","user":"51203146506d961c030791801","timestamp":"2020-06-05 12:00","time":"5"}'
```

```javascript
let jsonData = {
  createdByUser: '5f48eb3e65d7ee4942c46eeb',
  user: '51203146506d961c030791801',
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
  "_id": "5fbcfe75ba9312280ef6523e",
  "timestamp": "2020-11-19T12:00:00.000Z",
  "realTimestamp": "2020-11-19T12:00:00.000Z",
  "createDate": "2020-11-24T12:37:09.258Z",
  "unSocialHoursCosts": [],
  "customFields": [],
  "machineTimePrices": [],
  "machineTimeSupplements": [],
  "systemAccount": "5112826056d961c030000001",
  "user": "51203146506d961c030791801",
  "userName": "Tommy Hellström",
  "endTimestamp": "2020-11-19T17:00:00.000Z",
  "realEndTimestamp": "2020-11-19T17:00:00.000Z",
  "time": 5,
  "invoiceableTime": 5,
  "pricePerHour": 777,
  "price": 777,
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
timestamp           | String | Yes | Starting date and time for the time log. This must be in the format 'YYYY-MM-DD HH-MM'
endTimestamp        | String | No* | Starting date and time for the time log. This must be in the format 'YYYY-MM-DD HH-MM'. *This is required if field 'time' is not specified
time                | String | No* | time of the timelog in hours. *This is required if field 'endTimestamp' is not specified
invoiceableTime     | String | No  | Invoiceable time. If not specified, this will be set to the time of the time log
customer            | String | No  | Id of the customer
project             | String | No  | Id of the project
timeCategory        | String | No  | Id of the time category
workOrder           | String | No  | Id of the work order
pricePerHour        | Number | No  | price per hour of the time log. If not specified, the price will be set according to the user, customer, project, time category or work order.
description         | String | No  | Description/notes of the time log
internalDescription | String | No  | Internal description/notes of the time log
supplementOrder     | Boolean | No  | Is the time log a supplement order?
isInvoiceable       | Boolean | No  | Your order number

## Update a Time Log

```shell
  curl -X PUT "https://app.seventime.se/api/2/timeLogs/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"51203146506d961c030791801","modifiedByUser":"51718241fdb708f37959127","user":"51203146506d961c030791801","timestamp":"2020-10-7 07:00","endTimestamp":"2020-10-7 15:00"}'
```

```javascript
let jsonData = {
  _id: '5fbcfe75ba9312280ef6523e',
  modifiedByUser: '51718241fdb708f37959127',
  user: '51203146506d961c030791801',
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
  "_id": "5fbcfe75ba9312280ef6523e",
  "timestamp": "2020-10-07T06:00:00.000Z",
  "realTimestamp": "2020-10-07T06:00:00.000Z",
  "createDate": "2020-11-24T12:37:09.258Z",
  "unSocialHoursCosts": [],
  "customFields": [],
  "machineTimePrices": [],
  "machineTimeSupplements": [],
  "systemAccount": "5112826056d961c030000001",
  "user": "51203146506d961c030791801",
  "userName": "Tommy Hellström",
  "endTimestamp": "2020-10-07T014:00:00.000Z",
  "realEndTimestamp": "2020-10-07T14:00:00.000Z",
  "time": 8,
  "invoiceableTime": 8,
  "pricePerHour": 777,
  "price": 777,
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
  -d '{"_id":"51203146506d961c030791801"}'
```

```javascript
let jsonData = {
  _id: '5fbcfe75ba9312280ef6523e'
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
  "startLocation": { type: 'Point', coordinates: [] },
  "stopLocation": { type: 'Point', coordinates: [] },
  "allDay": false,
  "status": 1,
  "isInvoiceable": true,
  "isInvoiced": false,
  "_id": "5fbcfe75ba9312280ef6523e",
  "timestamp": "2020-10-07T06:00:00.000Z",
  "realTimestamp": "2020-10-07T06:00:00.000Z",
  "createDate": "2020-11-24T12:37:09.258Z",
  "unSocialHoursCosts": [],
  "customFields": [],
  "machineTimePrices": [],
  "machineTimeSupplements": [],
  "systemAccount": "5112826056d961c030000001",
  "user": "51203146506d961c030791801",
  "userName": "Tommy Hellström",
  "endTimestamp": "2020-10-07T014:00:00.000Z",
  "realEndTimestamp": "2020-10-07T14:00:00.000Z",
  "time": 8,
  "invoiceableTime": 8,
  "pricePerHour": 777,
  "price": 777,
}
"Time log deleted: _id: 5fbcfe75ba9312280ef6523e"
```

This endpoint deletes a time log

### HTTP Request

`DELETE https://app.seventime.se/api/2/timeLogs/`

### DELETE Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id             | String | Yes | Id of the time log


# Expenses 

## Get Expenses

```shell
curl "https://app.seventime.se/api/2/expenses/?limit=2&page=3" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/expenses/?&limit=2&page=3";
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
    "totalResources": 622,
    "totalPages": 311,
    "currentPage": 3
  },
  "data": [
    {
      "_id": "53ad291839f16d23a6414604d2",
      "attestedBy": null,
      "createDate": "2014-06-27T08:11:15.954Z",
      "customer": null,
      "customerName": "",
      "description": "",
      "documents": [],
      "expenseItem": "52d92f32d5fcf8941893174ab",
      "isAttested": false,
      "isInvoiceable": true,
      "isInvoiced": false,
      "name": "Arbetsordermodul2",
      "numberOfItems": 1,
      "project": "516fad2b265135db78024621§",
      "projectName": "Glimminge",
      "supplementOrder": false,
      "timestamp": "2014-06-27T00:00:00.000Z",
      "totalAmount": 20,
      "totalAmountAfterDiscount": 20,
      "totalAmountInclTax": 25,
      "totalTaxAmount": 5,
      "unit": "st",
      "unitCost": 20,
      "unitPrice": 20,
      "unitPriceInclTax": 25,
      "unitTax": 5,
      "user": "51203146506d961c030791801",
      "userName": "Tommy Hellström",
      "workOrder": null,
      "workOrderNumber": 0,
      "workOrderTitle": "",
      "unitPriceAfterDiscount": 20,
      "discountPercent": 0,
      "unitTaxPercent": 25,
      "doReimburse": false,
      "salaryCompilation": null,
      "verificationNumber": "",
      "distributor": null,
      "distributorName": "",
      "totalCost": 20,
      "articleNumber": "208"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves expenses, a maximum of 500 expenses will be returned.

### HTTP Request

`GET https://app.seventime.se/api/2/expenses`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
name               |  | If specified, expenses that match the parameter will be included.
articleNumber      |  | If specified, expenses that match the parameter will be included.
customer           |  | If specified, expenses that match the parameter will be included.
project            |  | If specified, expenses that match the parameter will be included.
distributor        |  | If specified, expenses that match the parameter will be included.
fromDate           |  | If specified, expenses registered after or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
toDate             |  | If specified, expenses registered before or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
sortBy             |  | If specified, a sort will be made on the specified parameter
sortDirection      |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending




## Get a specific Expense

```shell
curl "https://app.seventime.se/api/2/expenses/53ad291839f16d23a6414604d2" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/expenses/53ad291839f16d23a6414604d2";
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
    "_id": "53ad291839f16d23a6414604d2",
    "attestedBy": null,
    "createDate": "2014-06-27T08:11:15.954Z",
    "customer": null,
    "customerName": "",
    "description": "",
    "documents": [],
    "expenseItem": "52d92f32d5fcf8941893174ab",
    "isAttested": false,
    "isInvoiceable": true,
    "isInvoiced": false,
    "name": "Arbetsordermodul2",
    "numberOfItems": 1,
    "project": "516fad2b265135db78024621§",
    "projectName": "Glimminge",
    "supplementOrder": false,
    "timestamp": "2014-06-27T00:00:00.000Z",
    "totalAmount": 20,
    "totalAmountAfterDiscount": 20,
    "totalAmountInclTax": 25,
    "totalTaxAmount": 5,
    "unit": "st",
    "unitCost": 20,
    "unitPrice": 20,
    "unitPriceInclTax": 25,
    "unitTax": 5,
    "user": "51203146506d961c030791801",
    "userName": "Tommy Hellström",
    "workOrder": null,
    "workOrderNumber": 0,
    "workOrderTitle": "",
    "unitPriceAfterDiscount": 20,
    "discountPercent": 0,
    "unitTaxPercent": 25,
    "doReimburse": false,
    "salaryCompilation": null,
    "verificationNumber": "",
    "distributor": null,
    "distributorName": "",
    "totalCost": 20,
    "articleNumber": "208"
  }
}
```

This endpoint retrieves a specific expense.



### HTTP Request

`GET https://app.seventime.se/api/2/expenses/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the expense to retrieve

## Get Expenses Items

```shell
curl "https://app.seventime.se/api/2/expenseItems/?limit=10&page=176" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/expenseItems/?&limit=10&page=176";
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
    "totalResources": 19478,
    "totalPages": 1948,
    "currentPage": 176
  },
  "data": [
    {
      "_id": "5de78aed1332719192362bed",
      "description": "",
      "tax": 25,
      "articleNumber": "601310",
      "name": "10-pack Reaktionsbollar",
      "unitPrice": 295.59,
      "unitCost": 221,
      "unit": "St",
      "isInvoiceable": true,
      "isCategory": false,
      "parentExpenseItem": null,
      "parentExpenseItemName": "",
      "createDate": "2019-12-04T10:31:06.603Z",
      "bundledArticles": [],
      "alwaysReimburse": false,
      "isActive": true,
      "categoryGroupNumber": "",
      "articleGroupNumber": "",
      "distributor": null,
      "distributorName": "",
      "isInventoryItem": false,
      "unitPriceInclTax": 369.48749999999995
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves expense items, a maximum of 500 expense items will be returned.

### HTTP Request

`GET https://app.seventime.se/api/2/expenses`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
name                    |  | If specified, expense items that match the parameter will be included.
articleNumber           |  | If specified, expense items that match the parameter will be included.
distributorName         |  | If specified, expense items that match the parameter will be included.
description             |  | If specified, expense items that match the parameter will be included.
parentExpenseItemName   |  | If specified, expense items that match the parameter will be included.
isInvoiceable           |  | If specified, expense items that match the parameter will be included.
isActive                |  | If specified, expense items that match the parameter will be included.
favorite                |  | If specified, expense items that match the parameter will be included.
sortBy                  |  | If specified, a sort will be made on the specified parameter
sortDirection           |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending




## Get a specific Expense Item

```shell
curl "https://app.seventime.se/api/2/expenseItems/5de78aed1332719192362bed" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/expenseItems/5de78aed1332719192362bed";
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
    "_id": "5de78aed1332719192362bed",
    "description": "",
    "tax": 25,
    "articleNumber": "601310",
    "name": "10-pack Reaktionsbollar",
    "unitPrice": 295.59,
    "unitCost": 221,
    "unit": "St",
    "isInvoiceable": true,
    "isCategory": false,
    "parentExpenseItem": null,
    "parentExpenseItemName": "",
    "createDate": "2019-12-04T10:31:06.603Z",
    "bundledArticles": [],
    "alwaysReimburse": false,
    "isActive": true,
    "categoryGroupNumber": "",
    "articleGroupNumber": "",
    "distributor": null,
    "distributorName": "",
    "isInventoryItem": false,
    "unitPriceInclTax": 369.48749999999995
  }
}
```

This endpoint retrieves a specific expense item.



### HTTP Request

`GET https://app.seventime.se/api/2/expenseItems/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the expense item to retrieve


## Create an Expense

```shell
  curl -X POST "https://app.seventime.se/api/2/expenses/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"createdByUser":"5f48eb3e65d7ee4942c46eeb","user":"51203146506d961c030791801","expenseItem":"5de78aed1332719192362bed"}'
```

```javascript
let jsonData = {
  createdByUser: '5f48eb3e65d7ee4942c46eeb',
  user: '51203146506d961c030791801',
  expenseItem: '5de78aed1332719192362bed'
};

let options = {
  url: 'https://app.seventime.se/api/2/expenses',
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
    console.log("Expense created: _id: " + body._id);
  } else {
    console.error("ERROR! Unable to create expense: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "isInvoiceable": true,
  "_id": "5fbe684416625651d7f43257",
  "timestamp": "2020-11-25T14:20:52.129Z",
  "documents": [],
  "createDate": "2020-11-25T14:20:52.129Z",
  "bundledArticles": [],
  "customFields": [],
  "systemAccount": "5112826056d961c030000001",
  "numberOfItems": 1,
  "user": "51203146506d961c030791801",
  "userName": "Tommy Hellström",
  "expenseItem": "5de78aed1332719192362bed",
  "articleNumber": "575733",
  "name": "10-pack Reaktionsbollar",
  "description": "Skivhantel av järn",
  "distributor": "573c52cdf609f5692351914b",
  "distributorName": "Lev 4",
  "unit": "St",
  "unitCost": 319,
  "unitTaxPercent": 25,
  "unitPrice": 426.66,
  "unitPriceAfterDiscount": 426.66,
  "discountPercent": 0,
  "unitTax": 106.665,
  "unitPriceInclTax": 533.325,
  "totalTaxAmount": 106.665,
  "totalAmount": 426.66,
  "totalAmountAfterDiscount": 426.66,
  "totalCost": 319,
}
"Expense created: _id: 5fbe684416625651d7f43257"
```

This endpoint creates an expense

### HTTP Request

`POST https://app.seventime.se/api/2/expenses/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
createdByUser       | String | Yes | Id of the user who created the expense
user                | String | Yes | Id of the user on the expense
expenseItem         | String | Yes*| Id of the expense item. *Required if freetext for articles is not activated 
name                | String | Yes*| Name of the article. *Required if expenseItem is not specified. This will set the article to freetext and is only possible if the setting for this is enabled. 
workOrder           | String | No  | Id of the work order
customer            | String | No  | Id of the customer. If workOrder is specified, the customer from the work order will be used
project             | String | No  | Id of the project. If workOrder is specified, the project from the work order will be used
distributor         | String | No  | Id of the distributor
numberOfItems       | String | No  | Number of items
unit                | String | No  | Unit of the number of items
unitCost            | Number | No* | Cost per unit. If not specified, the cost on the expense item will be used. *Required if expenseItem is not specified
unitPrice           | Number | No* | Price per unit. If not specified, the price from the price list set on the customer will be used. If no price list is set, the price will be calculated from the cost and the 'Mark up on purchase price' on the customer. If 'Mark up on purchase price' is 0, the price will be set to the expense item price. *Required if expenseItem is not specified
discountPercent     | Number | No* | Discount percent on the unit price. *Required if expenseItem is not specified
taxPercent          | Number | No* | Tax percent on the unit price. *Required if expenseItem is not specified
timestamp           | String | No  | Time stamp of expense
description         | String | No  | Description of the expense
isInvoiceable       | Boolean | No | Is the expense invoiceable?
doReimburse         | Boolean | No | Is the expense an own expense?

## Update an Expense

```shell
  curl -X PUT "https://app.seventime.se/api/2/expenses/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fbe684416625651d7f43257","modifiedByUser":"5f48eb3e65d7ee4942c46eeb","user":"51203146506d961c030791801"}'
```

```javascript
let jsonData = {
  _id: '5fbe684416625651d7f43257',
  modifiedByUser: '5f48eb3e65d7ee4942c46eeb',
  user: '51203146506d961c030791801'
};

let options = {
  url: 'https://app.seventime.se/api/2/expenses',
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
    console.log("Expense updated: _id: " + body._id);
  } else {
    console.error("ERROR! Unable to update expense: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "isInvoiceable": true,
  "_id": "5fbe684416625651d7f43257",
  "timestamp": "2020-11-25T14:20:52.129Z",
  "documents": [],
  "createDate": "2020-11-25T14:20:52.129Z",
  "bundledArticles": [],
  "customFields": [],
  "systemAccount": "5112826056d961c030000001",
  "numberOfItems": 1,
  "user": "51203146506d961c030791801",
  "userName": "Tommy Hellström",
  "expenseItem": "5de78aed1332719192362bed",
  "articleNumber": "575733",
  "name": "10-pack Reaktionsbollar",
  "description": "Skivhantel av järn",
  "distributor": "573c52cdf609f5692351914b",
  "distributorName": "Lev 4",
  "unit": "St",
  "unitCost": 319,
  "unitTaxPercent": 25,
  "unitPrice": 426.66,
  "unitPriceAfterDiscount": 426.66,
  "discountPercent": 0,
  "unitTax": 106.665,
  "unitPriceInclTax": 533.325,
  "totalTaxAmount": 106.665,
  "totalAmount": 426.66,
  "totalAmountAfterDiscount": 426.66,
  "totalCost": 319,
}
"Expense updated: _id: 5fbe684416625651d7f43257"
```

This endpoint updates an expense

### HTTP Request

`PUT https://app.seventime.se/api/2/expenses/`

### PUT Parameters
The table below shows the required fields. Other available fields can be found in the section 'Create an Expense'.


Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id            | String | Yes | Id of the expense
modifiedByUser | String | Yes | Id of the user who made the change
user           | String | Yes | Id of the user on the expense

## Delete an Expense

```shell
  curl -X DELETE "https://app.seventime.se/api/2/expenses/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fbe684416625651d7f43257","deletedByUser":"51203146506d961c030791801"}'
```

```javascript
let jsonData = {
  _id: "5fbe684416625651d7f43257",
  deletedByUser: '51203146506d961c030791801'
};

let options = {
  url: 'https://app.seventime.se/api/2/expenses',
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
    console.log("Expense deleted: _id: " + body._id);
  } else {
    console.error("ERROR! Unable to delete expense: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "_id": "5fbe684416625651d7f43257"
}
"Expense deleted: _id: 5fbe684416625651d7f43257"
```

This endpoint deletes an expense

### HTTP Request

`DELETE https://app.seventime.se/api/2/expenses/`

### DELETE Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                | String | Yes | Id of the expense
deletedByUser      | String | Yes | Id of the user who deleted the expense


# Driver Journals
## Get Driver Journals

```shell
curl "https://app.seventime.se/api/2/driverJournals/limit=5&page=2" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/driverJournals/?&limit=5&page=2";
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
    "totalPages": 18,
    "currentPage": 2
  },
  "data": [
    {
      "_id": "5613c0eabed82c732b67914b",
      "name": "",
      "driverJournalItemType": "574ed84219e781253319275004d",
      "driverJournalItemTypeName": "4 kr/km",
      "car": null,
      "carRegistrationNumber": "ABC123",
      "description": "",
      "user": "5f48eb3e65d7ee4942c46eeb",
      "userName": "Tommy Hellström",
      "customer": "5bb26376c42fb99275000080",
      "customerName": "Hellapps AB",
      "project": "5f924f4f533f102af78f95b6",
      "projectName": "Tester",
      "workOrder": "5bae34dca878bd790d02065g",
      "workOrderTitle": "20160525",
      "workOrderNumber": 1181,
      "startAddress": "Glimmingevägen 18, Västra Karup",
      "endAddress": "Hamngatan 1, Malmö",
      "travelPurpose": ".",
      "startOdometer": 156,
      "endOdometer": 178,
      "totalDistance": 22,
      "price": 4,
      "totalAmount": 88,
      "isInvoiced": true,
      "invoice": "5fab29b038bd334ab540ab53",
      "modifiedDate": "2016-06-17T09:29:01.958Z",
      "createDate": "2016-06-17T09:20:46.845Z",
      "isInvoiceable": true,
      "timestamp": "2016-06-17T09:20:10.254Z",
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves driver journals, a maximum of 500 driver journals will be returned.

### HTTP Request

`GET https://app.seventime.se/api/2/driverJournals`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
projectName                 |  | If specified, driver journals that match the parameter will be included.
customerName                |  | If specified, driver journals that match the parameter will be included.
driverJournalItemTypeName   |  | If specified, driver journals that match the parameter will be included.
isInvoiceable               |  | If specified, driver journals that match the parameter will be included.
workOrderTitle              |  | If specified, driver journals that match the parameter will be included.
workOrderNumber             |  | If specified, driver journals that match the parameter will be included.
carRegistrationNumber       |  | If specified, driver journals that match the parameter will be included.
startAddress                |  | If specified, driver journals that match the parameter will be included.
endAddress                  |  | If specified, driver journals that match the parameter will be included.
fromDate                    |  | If specified, driver journals registered after or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
toDate                      |  | If specified, driver journals registered before or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
sortBy                      |  | If specified, a sort will be made on the specified parameter
sortDirection               |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending




## Get a specific Driver Journal

```shell
curl "https://app.seventime.se/api/2/driverJournals/5613c0eabed82c732b67914b" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/driverJournals/5613c0eabed82c732b67914b";
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
    "_id": "5613c0eabed82c732b67914b",
    "name": "",
    "driverJournalItemType": "574ed84219e781253319275004d",
    "driverJournalItemTypeName": "4 kr/km",
    "car": null,
    "carRegistrationNumber": "ABC123",
    "description": "",
    "user": "5f48eb3e65d7ee4942c46eeb",
    "userName": "Tommy Hellström",
    "customer": "5bb26376c42fb99275000080",
    "customerName": "Hellapps AB",
    "project": "5f924f4f533f102af78f95b6",
    "projectName": "Tester",
    "workOrder": "5bae34dca878bd790d02065g",
    "workOrderTitle": "20160525",
    "workOrderNumber": 1181,
    "startAddress": "Glimmingevägen 18, Västra Karup",
    "endAddress": "Hamngatan 1, Malmö",
    "travelPurpose": ".",
    "startOdometer": 156,
    "endOdometer": 178,
    "totalDistance": 22,
    "price": 4,
    "totalAmount": 88,
    "isInvoiced": true,
    "invoice": "5fab29b038bd334ab540ab53",
    "modifiedDate": "2016-06-17T09:29:01.958Z",
    "createDate": "2016-06-17T09:20:46.845Z",
    "timestamp": "2016-06-17T09:20:10.254Z",
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

let url = "https://app.seventime.se/api/2/driverJournalTypes/?";
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
      "_id": "5e5ef41f0d87d3262bc0176",
      "name": "Diesel - ej skt.fri",
      "articleNumber": "45",
      "cost": 0.5,
      "price": 0.65,
      "isInvoiceable": true,
      "isDefault": false,
      "salaryCompensationType": 20,
      "salaryType": "5e5cd96da2f5b43254aa1f1e",
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

This endpoint retrieves driver journals types, a maximum of 500 driver journals types will be returned.

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
  -d '{"createdByUser":"51203146506d961c030791801","user":"51203146506d961c030791801","expenseItem":"5de78aed1332719192362bed"}'
```

```javascript
let jsonData = {
  createdByUser: '51203146506d961c030791801',
  user: '5f48eb3e65d7ee4942c46eeb',
  carRegistrationNumber: 'ABC123',
  driverJournalItemType: '5e5ef41f0d87d3262bc0176',
  startAddress: 'Address start, V Karup',
  endAddress: 'Address end, Båstad',
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
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "isInvoiceable": true,
  "_id": "5fc619b96294735fc421d77a",
  "timestamp": "2020-12-01T10:23:53.370Z",
  "createDate": "2020-12-01T10:23:53.370Z",
  "modifiedDate": "2020-12-01T10:23:53.370Z",
  "systemAccount": "5112826056d961c030000001",
  "user": "5f48eb3e65d7ee4942c46eeb",
  "userName": "Tommy Hellström",
  "carRegistrationNumber": "ABC123",
  "driverJournalItemType": "5e5ef41f0d87d3262bc0176",
  "driverJournalItemTypeName": "Diesel - ej skt.fri",
  "startAddress": "Address start, V Karup",
  "endAddress": "Address end, Båstad",
  "travelPurpose": "Delivery",
  "startOdometer": 45,
  "endOdometer": 60,
  "totalDistance": 15,
  "isSalaryCompensated": false,
  "price": 0,
  "totalAmount": 0,
  "cost": 0,
  "totalCost": 0,
}
"Driver journal created: _id: 5fc619b96294735fc421d77a"
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
isInvoiceable           | Boolean | No | Is the driver jounal invoiceable?
isSalaryCompensated     | Boolean | No | Is the driver jounal salary compensated?

## Update a Driver Journal

```shell
  curl -X PUT "https://app.seventime.se/api/2/driverJournals/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fc619b96294735fc421d77a","modifiedByUser":"51203146506d961c030791801","user":"5f48eb3e65d7ee4942c46eeb"}'
```

```javascript
let jsonData = {
  _id: '5fc619b96294735fc421d77a',
  modifiedByUser: '51203146506d961c030791801',
  user: '5f48eb3e65d7ee4942c46eeb'
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
  "_id": "5fc619b96294735fc421d77a",
  "timestamp": "2020-12-01T10:23:53.370Z",
  "createDate": "2020-12-01T10:23:53.370Z",
  "modifiedDate": "2020-12-01T10:23:53.370Z",
  "systemAccount": "5112826056d961c030000001",
  "user": "5f48eb3e65d7ee4942c46eeb",
  "userName": "Tommy Hellström",
  "carRegistrationNumber": "ABC123",
  "driverJournalItemType": "5e5ef41f0d87d3262bc0176",
  "driverJournalItemTypeName": "Diesel - ej skt.fri",
  "startAddress": "Address start, V Karup",
  "endAddress": "Address end, Båstad",
  "travelPurpose": "Delivery",
  "startOdometer": 45,
  "endOdometer": 60,
  "totalDistance": 15,
  "isSalaryCompensated": false,
  "price": 0,
  "totalAmount": 0,
  "cost": 0,
  "totalCost": 0,
}
"Driver journal updated: _id: 5fc619b96294735fc421d77a"
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
user           | String | Yes | Id of the user

## Delete a Driver Journal

```shell
  curl -X DELETE "https://app.seventime.se/api/2/driverJournals/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fc619b96294735fc421d77a"}'
```

```javascript
let jsonData = {
  _id: '5fc619b96294735fc421d77a'
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
  "_id": "5fc619b96294735fc421d77a",
}
"Driver journal updated: _id: 5fc619b96294735fc421d77a"
```

This endpoint deletes a driver journal

### HTTP Request

`DELETE https://app.seventime.se/api/2/driverJournals/`

### DELETE Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                    | String | Yes | Id of the driver journal


# Vehicles
## Get Vehicles

```shell
curl "https://app.seventime.se/api/2/vehicles/?limit=5&page=2" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/vehicles/?&limit=5&page=2";
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
    "totalResources": 28,
    "totalPages": 6,
    "currentPage": 2
  },
  "data": [
    {
      "_id": "55782f0382da2f85430284d",
      "name": "Audi Q8",
      "registrationNumber": "ABC123",
      "isActive": true,
      "createDate": "2016-06-08T14:45:42.546Z",
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves vehicles, a maximum of 500 vehicles will be returned.

### HTTP Request

`GET https://app.seventime.se/api/2/vehicles`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy                      |  | If specified, a sort will be made on the specified parameter
sortDirection               |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


## Get a specific Vehicles

```shell
curl "https://app.seventime.se/api/2/vehicles/55782f0382da2f85430284d" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/vehicles/55782f0382da2f85430284d";
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
    "_id": "55782f0382da2f85430284d",
    "name": "Audi Q8",
    "registrationNumber": "ABC123",
    "isActive": true,
    "createDate": "2016-06-07T13:20:04.346Z",
  }
}
```

This endpoint retrieves a specific vehicle.


### HTTP Request

`GET https://app.seventime.se/api/2/vehicle/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the vehicle to retrieve

# Distributors
## Get Distributors

```shell
curl "https://app.seventime.se/api/2/distributors/?limit=5&page=3" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/distributors/?&limit=5&page=3";
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

This endpoint retrieves distributors, a maximum of 500 distributors will be returned.

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
curl "https://app.seventime.se/api/2/distributorContactPersons/?&distributor=5fca23df0317c3dae47b04a" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/distributorContactPersons/?&distributor=5fca23df0317c3dae47b04a";
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

This endpoint retrieves distributor contact persons, a maximum of 500 contact persons will be returned.

### HTTP Request

`GET https://app.seventime.se/api/2/distributorContactPersons/?&distributor=5fca23df0317c3dae47b04a`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
distributor                 |  | Id of the distributor. This field must be included
sortBy                      |  | If specified, a sort will be made on the specified parameter
sortDirection               |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

# Purchase Orders
## Get Purchase Orders

```shell
curl "https://app.seventime.se/api/2/purchaseOrders/?limit=2&page=5" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/purchaseOrders/?&limit=2&page=5";
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
    "totalResources": 70,
    "totalPages": 35,
    "currentPage": 5
  },
  "data": [
    {
      "_id": "59d6041d5551819581034002",
      "purchaseOrderNumber": "1009",
      "purchaseOrderName": "Beställning",
      "purchaseOrderInfoName": "ererer",
      "language": "SV",
      "headerText": "Vi önskar att beställa följande.",
      "footerText": "<table width=\"100%\"><tr><td style='vertical-align: top;'>FIRST</td><td style='vertical-align: top;'>SECOND</td></tr></table>",
      "footerInfoText": "",
      "createdByUser": "5f48eb3e65d7ee4942c46eeb",
      "createdByUserName": "Tommy Hellström",
      "ourReference": "5f48eb3e65d7ee4942c46eeb",
      "ourReferenceName": "Tommy Hellström",
      "approvedBy": null,
      "distributor": "5f6b2e6af24d5df55b69277",
      "distributorName": "Alheka",
      "distributorAddress": "Glimmingevägen 18<br>26974 Västra Karup",
      "distributorVAT": "",
      "ourCustomerNumber": "123456",
      "contactPersonDistributor": null,
      "contactPersonDistributorName": null,
      "project": null,
      "projectName": null,
      "workOrder": null,
      "workOrderName": "",
      "workOrderNumber": "0",
      "purchaseOrderDate": "2017-09-11T13:30:55.026Z",
      "totalAmount": 1000,
      "totalTaxAmount": 250,
      "totalAmountInclTax": 1250,
      "taxPercent": 25,
      "totalCost": 0,
      "currencyCode": "SEK",
      "currencyRate": 1,
      "purchaseOrderStatus": 4,
      "archived": false,
      "archivedDate": null,
      "sentDate": "2017-09-11T13:31:08.972Z",
      "confirmationDate": "2017-09-11T13:31:41.071Z",
      "desiredDeliveryDate": null,
      "expectedDeliveryDate": "2017-09-14T22:00:00.000Z",
      "paymentDays": 30,
      "marking": "",
      "deliveryAttention": "",
      "deliveryPhone": "",
      "publicLink": "l0qMb5V9L1uVMDHqBZ",
      "approvedByName": null,
      "invoiceAddress": {
        "address": "Glimmingevägen 18",
        "address2": "",
        "zipCode": "12345",
        "city": "V Karup",
        "country": "",
        "email": "",
        "name": "Hellapps"
      },
      "deliveryAddress": {
        "name": "",
        "address": "",
        "address2": "",
        "zipCode": "",
        "city": "",
        "country": "",
        "phone": ""
      },
      "documents": [],
      "purchaseOrderLogEntries": [
        {
          "_id": "5f48eb3e65d7ee4942c46eeb",
          "logType": 5,
          "description": "",
          "user": "59312765ad961c0318eb0a2",
          "userName": "Tommy Hellström",
          "logDate": "2017-09-11T13:31:08.972Z"
        },
        {
          // ...
        }
      ],
      "invoiceItems": [
        {
          // ...
        }
      ],
      "createDate": "2017-09-11T13:31:08.963Z",
      "projectNumber": "183897"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves purchase orders, a maximum of 500 purchase orders will be returned.

### HTTP Request

`GET https://app.seventime.se/api/2/purchaseOrders`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
purchaseOrderName                   |  | If specified, purchase orders that match the parameter will be included.
purchaseOrderInfoName               |  | If specified, purchase orders that match the parameter will be included.
purchaseOrderNumber                 |  | If specified, purchase orders that match the parameter will be included.
purchaseOrderStatus                 |  | If specified, purchase orders that match the parameter will be included.
distributor                         |  | If specified, purchase orders that match the parameter will be included.
project                             |  | If specified, purchase orders that match the parameter will be included.
workOrder                           |  | If specified, purchase orders that match the parameter will be included.
workOrderNumber                     |  | If specified, purchase orders that match the parameter will be included.
sortBy                              |  | If specified, a sort will be made on the specified parameter
sortDirection                       |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get a specific Purchase Order

```shell
curl "https://app.seventime.se/api/2/purchaseOrders/59d6041d5551819581034002" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/purchaseOrders/59d6041d5551819581034002";
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
    "deliveryAddress": {
      "name": "",
      "address": "",
      "address2": "",
      "zipCode": "",
      "city": "",
      "country": "",
      "phone": ""
    },
    "invoiceAddress": {
      "address": "Glimmingevägen 18",
      "address2": "",
      "zipCode": "12345",
      "city": "V Karup",
      "country": "",
      "email": "",
      "name": "Hellapps"
    },
    "_id": "59d6041d5551819581034002",
    "purchaseOrderNumber": "1009",
    "purchaseOrderName": "Beställning",
    "purchaseOrderInfoName": "ererer",
    "language": "SV",
    "headerText": "Vi önskar att beställa följande.",
    "footerText": "<table width=\"100%\"><tr><td style='vertical-align: top;'>FIRST</td><td style='vertical-align: top;'>SECOND</td></tr></table>",
    "footerInfoText": "",
    "createdByUser": "5f48eb3e65d7ee4942c46eeb",
    "createdByUserName": "Tommy Hellström",
    "ourReference": "5f48eb3e65d7ee4942c46eeb",
    "ourReferenceName": "Tommy Hellström",
    "approvedBy": null,
    "distributor": "5f6b2e6af24d5df55b69277",
    "distributorName": "Alheka",
    "distributorAddress": "Glimmingevägen 18<br>26974 Västra Karup",
    "distributorVAT": "",
    "ourCustomerNumber": "123456",
    "contactPersonDistributor": null,
    "contactPersonDistributorName": null,
    "project": null,
    "projectName": null,
    "workOrder": null,
    "workOrderName": "",
    "workOrderNumber": "0",
    "purchaseOrderDate": "2017-09-11T13:30:55.026Z",
    "totalAmount": 1000,
    "totalTaxAmount": 250,
    "totalAmountInclTax": 1250,
    "taxPercent": 25,
    "totalCost": 0,
    "currencyCode": "SEK",
    "currencyRate": 1,
    "purchaseOrderStatus": 4,
    "archived": false,
    "archivedDate": null,
    "sentDate": "2017-09-11T13:31:08.972Z",
    "confirmationDate": "2017-09-11T13:31:41.071Z",
    "desiredDeliveryDate": null,
    "expectedDeliveryDate": "2017-09-14T22:00:00.000Z",
    "paymentDays": 30,
    "marking": "",
    "deliveryAttention": "",
    "deliveryPhone": "",
    "publicLink": "l0qNw5V8L1uVMqoDRqbZ",
    "approvedByName": null,
    "documents": [],
    "purchaseOrderLogEntries": [
      {
        "logDate": "2017-09-11T13:31:08.972Z",
        "_id": "59b6901c1598211831000063",
        "logType": 5,
        "description": "",
        "user": "5f48eb3e65d7ee4942c46eeb",
        "userName": "Tommy Hellström"
      },
      {
        // ...
      }
    ],
    "invoiceItems": [
      {
        // ...
      }
    ],
    "createDate": "2017-09-11T13:31:08.963Z",
    "projectNumber": "183897"
  }
}
```

This endpoint retrieves a specific purchase order.


### HTTP Request

`GET https://app.seventime.se/api/2/purchaseOrders/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the purchase order to retrieve

## Create a Purchase Order

```shell
  curl -X POST "https://app.seventime.se/api/2/purchaseOrders/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"createdByUser":"51718241fdb708f37959127","distributor":"5f6b2e6af24d5df55b69277"}' 
```

```javascript
let jsonData = {
  createdByUser: '51718241fdb708f37959127',
  distributor: '5f6b2e6af24d5df55b69277',
};

let options = {
  url: 'https://app.seventime.se/api/2/purchaseOrders',
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
    console.log("Purchase Order updated: " + body.purchaseOrderName +  ", _id: " + body._id);
  } else {
    console.error("ERROR! Unable to create purchase order: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "deliveryAddress":
    { "name": "test namn",
      "address": "Glimmingevägen 18",
      "address2": "Testvägen 123",
      "zipCode": "12345",
      "city": "Västra Karup",
      "country": "SE" 
    },
    "invoiceAddress":
    { "name": "test namn",
      "address": "Glimmingevägen 18",
      "address2": "Testvägen 123",
      "zipCode": "12345",
      "city": "Västra Karup",
      "country": "SE",
      "email": "test@test.se" 
    },
  "_id": "5fca480e571eb873a64b97ec",
  "createDate": "2020-12-04T14:30:38.164Z",
  "invoiceItems": [],
  "purchaseOrderLogEntries":
    [ 
      { "_id": "5fca480e571eb873a64b97ed",
        "logType": 5,
        "description": "",
        "user": "51714655fbb708f379000003",
        "userName": "Lucas Hellström",
        "logDate": "2020-12-04T14:30:38.169Z" 
       } 
     ],
  "documents": [],
  "purchaseOrderName": "purchase Order 123",
  "purchaseOrderInfoName": "purchase order info 123",
  "deliveryAttention": "Tommy",
  "deliveryPhone": "123947513",
  "marking": "test mark",
  "headerText": "header text",
  "footerText": "footer text",
  "footerInfoText": "footer info text",
  "createdByUser": "51714655fbb708f379000003",
  "createdByUserName": "Lucas Hellström",
  "distributor": "5f6b4b6ef26b5d6f5a687207",
  "distributorName": "UE lev 20200923",
  "distributorAddress": "",
  "distributorVAT": "",
  "ourCustomerNumber": "",
  "language": "EN",
  "ourReference": "51714655fbb708f379000003",
  "ourReferenceName": "Lucas Hellström",
  "purchaseOrderStatus": 10,
  "contactPersonDistributor": "5fca0baf099b1c3ada47b04e",
  "contactPersonDistributorName": "dwd21",
  "purchaseOrderDate": "2020-12-04T23:00:00.000Z",
  "project": "5b20cce1d59a902e28000079",
  "projectName": "Blåsippan",
  "workOrder": "5fb3d3f6d2b1a732b1129213",
  "workOrderNumber": "4922",
  "workOrderName": "API test 4",
  "desiredDeliveryDate": "2020-12-19T23:00:00.000Z",
  "paymentDays": 5,
  "publicLink": "D2ymDeLqBpsOZDdJNVnV",
  "sentDate": "2020-12-04T14:30:38.169Z",
  "purchaseOrderNumber": "1051",
}
"Purchase Order created: name: purchase Order 123, _id: 5fca480e571eb873a64b97ec"
```

This endpoint creates a purchase order

### HTTP Request

`POST https://app.seventime.se/api/2/purchaseOrders/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
createdByUser             | String | Yes | Id of the user who created the purchase order
distributor               | String | Yes | Id of the distributor
language                  | String | No | Language of the purchase order as a language code, e.g 'SV' for Swedish
purchaseOrderName         | String | No | Name of the purchase order. If not specified, this will be set according to the settings
purchaseOrderInfoName     | String | No | Name of the info box on the purchase order. This will not be shown on the purchase order when sent
purchaseOrderStatus       | String | No | Purchase order status. See below for available statuses
contactPersonDistributor  | String | No | Id of the contact person of the distributor
purchaseOrderDate         | String | No | Purchase order date in the format 'YYYY-MM-DD'
workOrder                 | String | No | Id of the work order. The work order will only be shown in the info box and not on the purchase order when sent
project                   | String | No | Id of the project. The project will only be shown in the info box and not on the purchase order when sent
desiredDeliveryDate       | String | No | Desired delivery date
deliveryAddress           | Object | No | Contains attributes for delivery address. See below for details
deliveryAttention         | String | No | Id of the delivery attention
deliveryPhone             | String | No | Phone number of the delivery
invoiceAddress            | Object | No | Contains attributes for invoice address. See below for details
marking                   | String | No | Marking on the purchase order
paymentDays               | Number | No | Number of payment days
invoiceItems              | Array  | No | Array of objects which describe the invoice items on the purchase order. See below for details
headerText                | String | No | Header text that will be shown above the invoice rows
footerText                | String | No | Footer text that will be shown in the footer
footerInfoText            | String | No | Fotter info text that will be shown below the invoice rows

**Purchase order statuses**

Code | Description
--------- | ----------- 
1   | Draft
2   | Sent
3   | Obliterated
4   | Confirmed
10  | Delivered


**Attributes for deliveryAddress & invoiceAddress**

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
name                        | String | No | Name of delivery recipient
address                     | String | No | Primary address
address2                    | String | No | Secondary address
zipCode                     | String | No | Zip code
city                        | String | No | City
country                     | String | No | Country, given as a country code (E.g. SE for Sweden)
phone                       | String | No | Phone number



**Attributes for invoiceItems**

The field invoiceItems should be an array containing objects with the attributes shown below

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
itemType              | String | Yes | Item type of invoice row, see below for details
expenseItem           | String | No* | Id of the expense. *Required if itemType is expense
timeCategory          | String | No* | Id of the time category. *Required if itemType is timelog
numberOfItems         | Number | No  | Quantity of the item. If not specified, this will be set to 1
unit                  | String | No  | Unit of the item
unitPrice             | Number | No  | Unit price of the item
pricePerHour          | Number | No  | Price per hour. Used for time log rows
totalAmount           | Number | No  | Total amount. Used for onlyamount rows
discountPercent       | Number | No  | Discount of the item

**Item types**

This table contains the different item types used in the field invoiceItems.itemTypes

Item type |  Description
--------- |-----------
expense        | Expense row
timeLog        | Time log row
general        | Free-text row
blank          | Blank row
text           | Text row
onlyamount     | Text+amount row

## Update a Purchase Order

```shell
  curl -X PUT "https://app.seventime.se/api/2/purchaseOrders/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fca480e571eb873a64b97ec","modifiedByUser":"51718241fdb708f37959127","paymentDays":"10"}' 
```

```javascript
let jsonData = {
  _id: '5fca480e571eb873a64b97ec',
  modifiedByUser: '51718241fdb708f37959127',
  paymentDays: 10
};

let options = {
  url: 'https://app.seventime.se/api/2/purchaseOrders',
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
    console.log("Purchase Order updated: " + body.purchaseOrderName +  ", _id: " + body._id);
  } else {
    console.error("ERROR! Unable to update purchase order: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "deliveryAddress":
    { "name": "test namn",
      "address": "Glimmingevägen 18",
      "address2": "Testvägen 123",
      "zipCode": "12345",
      "city": "Västra Karup",
      "country": "SE" 
    },
    "invoiceAddress":
    { "name": "test namn",
      "address": "Glimmingevägen 18",
      "address2": "Testvägen 123",
      "zipCode": "12345",
      "city": "Västra Karup",
      "country": "SE",
      "email": "test@test.se" 
    },
  "_id": "5fca480e571eb873a64b97ec",
  "createDate": "2020-12-04T14:30:38.164Z",
  "invoiceItems": [],
  "purchaseOrderLogEntries":
    [ 
      { "_id": "5fca480e571eb873a64b97ed",
        "logType": 5,
        "description": "",
        "user": "51714655fbb708f379000003",
        "userName": "Lucas Hellström",
        "logDate": "2020-12-04T14:30:38.169Z" 
       } 
     ],
  "documents": [],
  "purchaseOrderName": "purchase Order 123",
  "purchaseOrderInfoName": "purchase order info 123",
  "deliveryAttention": "Tommy",
  "deliveryPhone": "123947513",
  "marking": "test mark",
  "headerText": "header text",
  "footerText": "footer text",
  "footerInfoText": "footer info text",
  "createdByUser": "51714655fbb708f379000003",
  "createdByUserName": "Lucas Hellström",
  "distributor": "5f6b4b6ef26b5d6f5a687207",
  "distributorName": "UE lev 20200923",
  "distributorAddress": "",
  "distributorVAT": "",
  "ourCustomerNumber": "",
  "language": "EN",
  "ourReference": "51714655fbb708f379000003",
  "ourReferenceName": "Lucas Hellström",
  "purchaseOrderStatus": 10,
  "contactPersonDistributor": "5fca0baf099b1c3ada47b04e",
  "contactPersonDistributorName": "dwd21",
  "purchaseOrderDate": "2020-12-04T23:00:00.000Z",
  "project": "5b20cce1d59a902e28000079",
  "projectName": "Blåsippan",
  "workOrder": "5fb3d3f6d2b1a732b1129213",
  "workOrderNumber": "4922",
  "workOrderName": "API test 4",
  "desiredDeliveryDate": "2020-12-19T23:00:00.000Z",
  "paymentDays": 10,
  "publicLink": "D2ymDeLqBpsOZDdJNVnV",
  "sentDate": "2020-12-04T14:30:38.169Z",
  "purchaseOrderNumber": "1051",
}
"Purchase Order updated: name: purchase Order 123, _id: 5fca480e571eb873a64b97ec"

```

This endpoint updates a purchase order

### HTTP Request

`PUT https://app.seventime.se/api/2/purchaseOrders/`

### PUT Parameters
The table below shows the required fields. Other available fields can be found in the section 'Create a Purchase Order'.

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                        | String | Yes | Id of the purchase order
modifiedByUser             | String | Yes | Id of the user who modified the purchase order

## Delete a Purchase Order

```shell
  curl -X DELETE "https://app.seventime.se/api/2/purchaseOrders/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fca480e571eb873a64b97ec"}' 
```

```javascript
let jsonData = {
  _id: '5fca480e571eb873a64b97ec'
};

let options = {
  url: 'https://app.seventime.se/api/2/purchaseOrders',
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
    console.log("Purchase Order deleted: " + body.purchaseOrderName +  ", _id: " + body._id);
  } else {
    console.error("ERROR! Unable to delete purchase order: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "_id": "5fca480e571eb873a64b97ec",
  "purchaseOrderName": "purchase Order 123",
  "purchaseOrderNumber": "1051",
}
"Purchase Order deleted: name: purchase Order 123, _id: 5fca480e571eb873a64b97ec"

```

This endpoint deletes a purchase order

### HTTP Request

`DELETE https://app.seventime.se/api/2/purchaseOrders/`

### DELETE Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                        | String | Yes | Id of the purchase order

# Result Unit
## Get Result Units

```shell
curl "https://app.seventime.se/api/2/resultUnits" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/resultUnits/?";
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
      "_id": "57076abe8010bd22792004b",
      "name": "Kontor Syd",
      "code": "Syd",
      "isActive": true,
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves purchase orders.

### HTTP Request

`GET https://app.seventime.se/api/2/resultUnits`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy                              |  | If specified, a sort will be made on the specified parameter
sortDirection                       |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get a specific Result Unit

```shell
curl "https://app.seventime.se/api/2/resultUnits/57076abe8010bd22792004b" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/resultUnits/57076abe8010bd22792004b";
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
    "_id": "57076abe8010bd22792004b",
    "name": "Kontor Syd",
    "code": "Syd",
    "isActive": true,
  }
}
```

This endpoint retrieves a specific result unit.


### HTTP Request

`GET https://app.seventime.se/api/2/resultUnits/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the result unit to retrieve

# Quote
## Get Quotes

```shell
curl "https://app.seventime.se/api/2/quotes/?limit=5&page=5" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/quotes/?&limit=5&page=5";
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
    "totalResources": 195,
    "totalPages": 98,
    "currentPage": 5
  },
  "data": [
    {
      "_id": "5c33891321361d7d5235d294",
      "quoteNumber": "1054",
      "quoteType": 0,
      "quoteName": "Prisindikation",
      "quoteInfoName": "",
      "quoteCategory": null,
      "quoteCategoryName": null,
      "language": "SV",
      "description": null,
      "headerText": null,
      "footerInfoText": null,
      "footerText": "<table width=\"100%\"><tr><td style='vertical-align: top;'>TESTerrt</td><td style='vertical-align: top;'>TEST2</td><td style='vertical-align: top;'>TEST3</td></tr></table>",
      "createdByUser": "5f48eb3e65d7ee4942c46eeb",
      "createdByUserName": "Tommy Hellström",
      "ourReference": "5f48eb3e65d7ee4942c46eeb",
      "ourReferenceName": "Tommy Hellström",
      "salesAgent": "5f48eb3e65d7ee4942c46eeb",
      "salesAgentName": "Tommy Hellström",
      "customer": "5bb26376c42fb99275000080",
      "customerName": "Hellapps",
      "customerNumber": "44312",
      "customerAddress": "Glimmingevägen 18 26974 Västra Karup",
      "customerVAT": "",
      "contactPerson": null,
      "contactPersonName": null,
      "project": null,
      "projectName": null,
      "workOrder": null,
      "workOrderName": "",
      "workOrderNumber": "",
      "quoteDate": "2019-01-07T17:13:55.271Z",
      "validToDate": "2019-02-06T17:13:55.383Z",
      "discountInPercent": 0,
      "totalAmount": 500,
      "totalTaxAmount": 125,
      "totalAmountInclTax": 625,
      "taxPercent": 25,
      "totalCost": 0,
      "useQuoteValue": false,
      "quoteValue": 0,
      "useQuoteCost": false,
      "quoteCost": 0,
      "currencyCode": "SEK",
      "currencyRate": 1,
      "quoteStatus": 3,
      "archived": false,
      "archivedDate": null,
      "deliveryDate": null,
      "deliveryDateEnd": null,
      "sentDate": "2019-01-07T17:15:10.109Z",
      "acceptedDate": "2019-01-07T00:00:00.000Z",
      "rejectedDate": null,
      "invoice": null,
      "invoiceNumber": "",
      "invoicedDate": null,
      "priceList": null,
      "priceListName": "",
      "marking": "",
      "houseDeductionBasisAmount": 0,
      "houseDeductionAmount": 0,
      "enableQuoteConditions": false,
      "quoteConditionsContent": "<div>Leveransvillkor: Enligt PROCLAD Scandinavia allmänna leverans- och försäljningsvillkor.</div><div>Leveranstid: Enligt senare överenskommelse. Vi reservera oss för eventuell mellanförsäljning.</div><div>Frakt: frakt tillkommer enligt PROCLAD's prislista.</div><div>Priser: Alla priser är i SEK exklusive Moms.&nbsp;</div><div>Giltighet: Priserna gäller&nbsp;30 dagar efter&nbsp;offertdatum</div>",
      "multipleTaxesOnRows": false,
      "showPriceInclTaxesOnRows": true,
      "confirmationDate": null,
      "confirmationHeaderText": "Härmed bekräftar vi er beställning enligt specifikationen nedan.",
      "confirmationFooterInfoText": "Tack för er beställning!\n\nLeveransvillkor: enligt PROCLAD Scandinavia leverans- och försäljningsvillkor.\nBetalning: 30 dagar netto",
      "confirmationTitle": "Orderbekräftelse",
      "publicLink": "ObLBZZ0wDWcjlx7Be516",
      "useBudgetCalculation": false,
      "quoteAcceptReason": null,
      "quoteAcceptReasonName": null,
      "quoteDeclineReason": null,
      "quoteDeclineReasonName": null,
      "notes": "",
      "openNotificationSent": false,
      "quoteTemplate": "5b7dd2ba41cb2a725326s80",
      "stockReservationIsDone": false,
      "quoteElements": [
        {
          "_id": "5b7ada8bc41cb2341681",
          "content": {
            "text": "Hej!\nTack för er förfrågan. Vi har härmed möjligheten att offerera fasadtillbehör enligt nedan:\n\nHar tak? - \nHar fönster? - ",
            "confirmationText": "Hej!\nTack för er förfrågan. Vi har härmed möjligheten att offerera fasadtillbehör enligt nedan:\n\nHar tak? - \nHar fönster? - "
          },
          "backgroundColor": "FAFAFA",
          "bottomMargin": 20,
          "topMargin": 20,
          "elementTypeId": 1000,
          "itemId": "0.1735729354019433"
        },
        {
          "_id": "5c25fd4e818921172d237086",
          "content": {
            "invoiceItems": [
              {
                "stockLocation": "5bbd3a49dda7dbc37293680",
                "editMode": true,
                "selectedFlag": false,
                "houseWorkTypeOfWork": 0,
                "houseWorkFlag": false,
                "totalCost": 0,
                "totalAmountInclTax": 0,
                "totalTaxAmount": 0,
                "totalAmount": 500,
                "taxPercent": 25,
                "discountPercent": 0,
                "supplementChargePercent": 0,
                "discountInPercent": 0,
                "unitCost": 0,
                "unit": "Styck",
                "priceListName": null,
                "priceList": null,
                "unitPrice": 100,
                "numberOfItems": "5",
                "machineName": "",
                "machine": null,
                "driverJournalItemTypeName": "",
                "driverJournalItemType": null,
                "expenseItemName": "Seven Time - 5 användare - #2",
                "expenseItem": "5de78aed1332719192362bed",
                "categoryName": "",
                "timeCategory": null,
                "itemType": "expense",
                "createDate": null,
                "articleNumber": "203",
                "itemOrder": 1024,
                "itemId": "0.29956387071628154",
                "description": "",
                "name": "",
                "_id": null
              }
            ],
            "totalAmount": 500,
            "totalTaxAmount": 125,
            "totalAmountInclTax": 625,
            "taxPercent": 25,
            "totalCost": 0,
            "houseDeductionBasisAmount": 0,
            "houseDeductionAmount": 0,
            "selectableRows": false,
            "showOnlyTotalPrice": false,
            "hiddenColumns": [
              "articleNumber"
            ]
          },
          "backgroundColor": "FAFAFA",
          "bottomMargin": 20,
          "topMargin": 20,
          "elementTypeId": 1200,
          "itemId": "0.086780107201752"
        },
        {
          "_id": "5b7a808bc41361d87a3",
          "content": {
            "text": "Leveransvillkor: Enligt PROCLAD Scandinavia allmänna leverans- och försäljningsvillkor.\nLeveranstid: Enligt senare överenskommelse. Vi reservera oss för eventuell mellanförsäljning.\nFrakt: frakt tillkommer enligt PROCLAD's prislista.\nPriser: Alla priser är i SEK exklusive Moms. \nGiltighet: Priserna gäller 30 dagar efter offertdatum",
            "confirmationText": "Tack för er beställning!\n\nLeveransvillkor: enligt PROCLAD Scandinavia leverans- och försäljningsvillkor.\nBetalning: 30 dagar netto"
          },
          "backgroundColor": "FAFAFA",
          "bottomMargin": 20,
          "topMargin": 20,
          "elementTypeId": 1000,
          "itemId": "0.047508293157285886"
        }
      ],
      "budgetCalculation": {
        "invoiceItems": [],
        "totalBenefitAmount": 0,
        "totalCostAmount": 0
      },
      "houseProperties": {
        "typeOfProperty": 1,
        "propertyDescription": "",
        "housingSocietyNumber": "",
        "apartmentNumber": "",
        "maxDeductionAmount": 50000,
        "personalNumber": "",
        "deductionDistribution": []
      },
      "deliveryAddress": {
        "name": "",
        "address": "",
        "address2": "",
        "zipCode": "",
        "city": "",
        "country": "",
        "phone": ""
      },
      "documents": [],
      "quoteLogEntries": [
        {
          "_id": "5c33831c3512857d5cd6195",
          "logDate": "2019-01-07T17:15:08.533Z",
          "userName": "Tommy Hellström",
          "user": "59312765ad961c0318eb0a2",
          "description": "",
          "logType": 1,
          "entryId": "mZjaXWo2oRTr"
        },
        {
          // ...
        }
      ],
      "invoiceItems": [],
      "createDate": "2019-01-07T17:15:08.532Z",
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves quotes, a maximum of 500 quotes will be returned.

### HTTP Request

`GET https://app.seventime.se/api/2/quotes`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
quoteName                           |  | If specified, quotes that match the parameter will be included.
quoteNumber                         |  | If specified, quotes that match the parameter will be included.
fromQuoteDate                       |  | If specified, invoices with quote date after or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
toQuoteDate                         |  | If specified, invoices with quote date before or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
fromValidToDate                     |  | If specified, invoices with valid to date after or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
toValidToDate                       |  | If specified, invoices with valid to date before or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
sortBy                              |  | If specified, a sort will be made on the specified parameter
sortDirection                       |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get a specific Quote

```shell
curl "https://app.seventime.se/api/2/quotes/5c33891321361d7d5235d294" \
  -H "Client-Secret: thisismysecretkey" \ 
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/quotes/5c33891321361d7d5235d294";
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
    "_id": "5c33891321361d7d5235d294",
    "quoteNumber": "1054",
    "quoteType": 0,
    "quoteName": "Prisindikation",
    "quoteInfoName": "",
    "quoteCategory": null,
    "quoteCategoryName": null,
    "language": "SV",
    "description": null,
    "headerText": null,
    "footerInfoText": null,
    "footerText": "<table width=\"100%\"><tr><td style='vertical-align: top;'>TESTerrt</td><td style='vertical-align: top;'>TEST2</td><td style='vertical-align: top;'>TEST3</td></tr></table>",
    "createdByUser": "5f48eb3e65d7ee4942c46eeb",
    "createdByUserName": "Tommy Hellström",
    "ourReference": "5f48eb3e65d7ee4942c46eeb",
    "ourReferenceName": "Tommy Hellström",
    "salesAgent": "5f48eb3e65d7ee4942c46eeb",
    "salesAgentName": "Tommy Hellström",
    "customer": "5bb26376c42fb99275000080",
    "customerName": "Hellapps",
    "customerNumber": "44312",
    "customerAddress": "Glimmingevägen 18 26974 Västra Karup",
    "customerVAT": "",
    "contactPerson": null,
    "contactPersonName": null,
    "project": null,
    "projectName": null,
    "workOrder": null,
    "workOrderName": "",
    "workOrderNumber": "",
    "quoteDate": "2019-01-07T17:13:55.271Z",
    "validToDate": "2019-02-06T17:13:55.383Z",
    "discountInPercent": 0,
    "totalAmount": 500,
    "totalTaxAmount": 125,
    "totalAmountInclTax": 625,
    "taxPercent": 25,
    "totalCost": 0,
    "useQuoteValue": false,
    "quoteValue": 0,
    "useQuoteCost": false,
    "quoteCost": 0,
    "currencyCode": "SEK",
    "currencyRate": 1,
    "quoteStatus": 3,
    "archived": false,
    "archivedDate": null,
    "deliveryDate": null,
    "deliveryDateEnd": null,
    "sentDate": "2019-01-07T17:15:10.109Z",
    "acceptedDate": "2019-01-07T00:00:00.000Z",
    "rejectedDate": null,
    "invoice": null,
    "invoiceNumber": "",
    "invoicedDate": null,
    "priceList": null,
    "priceListName": "",
    "marking": "",
    "houseDeductionBasisAmount": 0,
    "houseDeductionAmount": 0,
    "enableQuoteConditions": false,
    "quoteConditionsContent": "<div>Leveransvillkor: Enligt PROCLAD Scandinavia allmänna leverans- och försäljningsvillkor.</div><div>Leveranstid: Enligt senare överenskommelse. Vi reservera oss för eventuell mellanförsäljning.</div><div>Frakt: frakt tillkommer enligt PROCLAD's prislista.</div><div>Priser: Alla priser är i SEK exklusive Moms.&nbsp;</div><div>Giltighet: Priserna gäller&nbsp;30 dagar efter&nbsp;offertdatum</div>",
    "multipleTaxesOnRows": false,
    "showPriceInclTaxesOnRows": true,
    "confirmationDate": null,
    "confirmationHeaderText": "Härmed bekräftar vi er beställning enligt specifikationen nedan.",
    "confirmationFooterInfoText": "Tack för er beställning!\n\nLeveransvillkor: enligt PROCLAD Scandinavia leverans- och försäljningsvillkor.\nBetalning: 30 dagar netto",
    "confirmationTitle": "Orderbekräftelse",
    "publicLink": "ObLBZZ0wDWcjlx7Be516",
    "useBudgetCalculation": false,
    "quoteAcceptReason": null,
    "quoteAcceptReasonName": null,
    "quoteDeclineReason": null,
    "quoteDeclineReasonName": null,
    "notes": "",
    "openNotificationSent": false,
    "quoteTemplate": "5b7dd2ba41cb2a725326s80",
    "stockReservationIsDone": false,
    "quoteElements": [
      {
        "_id": "5b7ada8bc41cb2341681",
        "content": {
          "text": "Hej!\nTack för er förfrågan. Vi har härmed möjligheten att offerera fasadtillbehör enligt nedan:\n\nHar tak? - \nHar fönster? - ",
          "confirmationText": "Hej!\nTack för er förfrågan. Vi har härmed möjligheten att offerera fasadtillbehör enligt nedan:\n\nHar tak? - \nHar fönster? - "
        },
        "backgroundColor": "FAFAFA",
        "bottomMargin": 20,
        "topMargin": 20,
        "elementTypeId": 1000,
        "itemId": "0.1735729354019433"
      },
      {
        "_id": "5c25fd4e818921172d237086",
        "content": {
          "invoiceItems": [
            {
              "stockLocation": "5bbd3a49dda7dbc37293680",
              "editMode": true,
              "selectedFlag": false,
              "houseWorkTypeOfWork": 0,
              "houseWorkFlag": false,
              "totalCost": 0,
              "totalAmountInclTax": 0,
              "totalTaxAmount": 0,
              "totalAmount": 500,
              "taxPercent": 25,
              "discountPercent": 0,
              "supplementChargePercent": 0,
              "discountInPercent": 0,
              "unitCost": 0,
              "unit": "Styck",
              "priceListName": null,
              "priceList": null,
              "unitPrice": 100,
              "numberOfItems": "5",
              "machineName": "",
              "machine": null,
              "driverJournalItemTypeName": "",
              "driverJournalItemType": null,
              "expenseItemName": "Seven Time - 5 användare - #2",
              "expenseItem": "5de78aed1332719192362bed",
              "categoryName": "",
              "timeCategory": null,
              "itemType": "expense",
              "createDate": null,
              "articleNumber": "203",
              "itemOrder": 1024,
              "itemId": "0.29956387071628154",
              "description": "",
              "name": "",
              "_id": null
            }
          ],
          "totalAmount": 500,
          "totalTaxAmount": 125,
          "totalAmountInclTax": 625,
          "taxPercent": 25,
          "totalCost": 0,
          "houseDeductionBasisAmount": 0,
          "houseDeductionAmount": 0,
          "selectableRows": false,
          "showOnlyTotalPrice": false,
          "hiddenColumns": [
            "articleNumber"
          ]
        },
        "backgroundColor": "FAFAFA",
        "bottomMargin": 20,
        "topMargin": 20,
        "elementTypeId": 1200,
        "itemId": "0.086780107201752"
      },
      {
        "_id": "5b7a808bc41361d87a3",
        "content": {
          "text": "Leveransvillkor: Enligt PROCLAD Scandinavia allmänna leverans- och försäljningsvillkor.\nLeveranstid: Enligt senare överenskommelse. Vi reservera oss för eventuell mellanförsäljning.\nFrakt: frakt tillkommer enligt PROCLAD's prislista.\nPriser: Alla priser är i SEK exklusive Moms. \nGiltighet: Priserna gäller 30 dagar efter offertdatum",
          "confirmationText": "Tack för er beställning!\n\nLeveransvillkor: enligt PROCLAD Scandinavia leverans- och försäljningsvillkor.\nBetalning: 30 dagar netto"
        },
        "backgroundColor": "FAFAFA",
        "bottomMargin": 20,
        "topMargin": 20,
        "elementTypeId": 1000,
        "itemId": "0.047508293157285886"
      }
    ],
    "budgetCalculation": {
      "invoiceItems": [],
      "totalBenefitAmount": 0,
      "totalCostAmount": 0
    },
    "houseProperties": {
      "typeOfProperty": 1,
      "propertyDescription": "",
      "housingSocietyNumber": "",
      "apartmentNumber": "",
      "maxDeductionAmount": 50000,
      "personalNumber": "",
      "deductionDistribution": []
    },
    "deliveryAddress": {
      "name": "",
      "address": "",
      "address2": "",
      "zipCode": "",
      "city": "",
      "country": "",
      "phone": ""
    },
    "documents": [],
    "quoteLogEntries": [
      {
        "_id": "5c33831c3512857d5cd6195",
        "logDate": "2019-01-07T17:15:08.533Z",
        "userName": "Tommy Hellström",
        "user": "59312765ad961c0318eb0a2",
        "description": "",
        "logType": 1,
        "entryId": "mZjaXWo2oRTr"
      },
      {
        // ...
      }
    ],
    "invoiceItems": [],
    "createDate": "2019-01-07T17:15:08.532Z",
  }
}
```

This endpoint retrieves a specific quote.


### HTTP Request

`GET https://app.seventime.se/api/2/quotes/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the quote to retrieve

## Get Quote Templates

```shell
curl "https://app.seventime.se/api/2/quoteTemplates" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/quoteTemplates/?";
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
      "_id": "5fb02816ed7ed72d9d936a0fa",
      "columnContents": [
        "This is a new footer!<br><br>"
      ],
      "templateName": "Standard utan sektioner",
      "quoteType": 0,
      "language": "",
      "createdByUser": "5f48eb3e65d7ee4942c46eeb",
      "createdByUserName": "Tommy Hellström",
      "createDate": "2020-11-09T13:31:10.929Z",
      "documents": [],
      "quoteElements": [
        {
          "_id": "5b7a808bc41cb2a725000081",
          "itemId": "0.2991772478801382",
          "elementTypeId": 1400,
          "topMargin": 20,
          "bottomMargin": 20,
          "backgroundColor": "FAFAFA",
          "content": null
        }
      ],
      "overrideFooter": false,
      "footerText": "<table width=\"100%\"><tr><td style='vertical-align: top;'>This is a new footer!<br><br></td></tr></table>",
      "footerNumOfCols": 1,
      "overrideLogoAndAddress": false,
      "logo": [
        {
          "_id": "5f6b5b15468263005f22404f3",
          "createDate": "2020-09-23T14:26:29.655Z",
          "modifiedDate": "2020-09-23T14:26:29.655Z",
          "name": "logo-med-beskrivande-text-caps-black-text-w300.png",
          "path": "https://seventimedev.s3-eu-west-1.amazonaws.com/5112826056d961c030000001/quoteTemplates/5f6b45ac31d0496b82642951/logo/logo-med-beskrivande-text-caps-black-text-w300.png?AWSAccessKeyId=AKIAIS4KY6NEYJKCBSGA&Expires=1605360649&Signature=kVutB84nfsqrmqCpHsAL3AGX4q8%3D",
          "contentType": "image/png",
          "size": 6765,
          "user": "5f48eb3e65d7ee4942c46eeb",
          "userName": "Tommy Hellström"
        }
      ],
      "logotypeWidth": 200,
      "logoPosition": "left",
      "quoteAddress": "<b>Företaget</b><div>Gatan</div><div>12345 Staden</div>",
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves quote templates.

### HTTP Request

`GET https://app.seventime.se/api/2/quoteTemplates`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
templateName                        |  | If specified, quote templates that match the parameter will be included.
sortBy                              |  | If specified, a sort will be made on the specified parameter
sortDirection                       |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get Quote Categories

```shell
curl "https://app.seventime.se/api/2/quoteCategories" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/quoteCategories/?";
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
      "_id": "58a678badc33073a42e02802",
      "isActive": true,
      "quoteCategoryName": "Utbildning"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves quote categories.

### HTTP Request

`GET https://app.seventime.se/api/2/quoteCategories`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
quoteCategoryName                   |  | If specified, quote categories that match the parameter will be included.
sortBy                              |  | If specified, a sort will be made on the specified parameter
sortDirection                       |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

# Custom fields
## Get Custom fields

```shell
curl "https://app.seventime.se/api/2/customFields/?&entityType=200" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/customFields/?&entityType=200";
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
    { "_id": "572cc7advab059714hcfca51",
      "selectFieldData": [],
      "fieldType": 100,
      "fieldName": "Kund",
      "include": true,
      "required": false },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves custom fields.

### HTTP Request

`GET https://app.seventime.se/api/2/customFields/?&entityType=<entityType>`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
entityType                          | 100 | Number corresponding to entity type. See table below for available types.

**Entity types**

Code | Description
--------- | ----------- 
100   | Time log
200   | Work order
300   | Tasks
400   | Invoice
500   | Project
600   | Expense
700   | Machine time log
800   | Driver journal
900   | Salary deviation
1000   | User
1100   | Customer
1200   | Absence
1300   | Work time absence
1400   | Quote
1500   | Machine
1600   | Object item
1700   | Customer signature
1800   | Supplement order
1900   | Construction diary
2000   | Checklist
2100   | Payment plan




