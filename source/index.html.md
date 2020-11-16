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
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Send Client-Secret in the header. Sample with the request library */

let options = { 
  headers: {
    "Client-Secret": "thisismysecretkey"
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

# Customers

## Get Customers


```shell
curl "https://app.seventime.se/api/1/customers" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/customers/?";
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
[
  {
    "_id": "5bb26376c42fb99275000080",
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
    "__v": 0,
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
```

This endpoint retrieves customers, a maximum of 100 customers will be returned.

### HTTP Request

`GET https://app.seventime.se/api/1/customers`

### Query Parameters

E.g. `https://app.seventime.se/api/1/customers/?organizationNumber=555555-5555` 

Parameter | Default | Description
--------- | ------- | -----------
name |  | If specified, customers that match the parameter will be included.
customerNumber |  | If specified, customers that match the parameter will be included.
organizationNumber |  | If specified, customers that match the parameter will be included.
city |  | If specified, customers that match the parameter will be included.
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


<!--<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>-->

## Get a Specific Customer

```shell
curl "https://app.seventime.se/api/1/customers/5bb26376c42fb99275000080" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/customers/5bb26376c42fb99275000080";
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
  "_id": "5bb26376c42fb99275000080",
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
  "__v": 0,
  "address2": "",
  "country": "",
  "billingMethod": "",
  "pricePerHour": 0,
  "paymentDays": 20,
  "notes": "",
  "isActive": true
}
```

This endpoint retrieves a specific customer.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/customers/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the customer to retrieve
  
  
## Create a Customer


```shell
  curl -X POST "https://app.seventime.se/api/1/customers/" \
  -H "Client-Secret: thisismysecretkey" \
  -d "name=Tommy Hellström&address=Glimmingevägen 18&zipCode=269 74&city=Västra Karup&phone=0431-360050&email=support@seventime.se&organizationNumber=555555-5555" 
```

```javascript
let formData = {
  name: 'Tommy Hellström',
  address: 'Glimmingevägen 18',
  zipCode: '269 74',
  city: 'Västra Karup',
  phone: '0431-360050',
  email: 'support@seventime.se',
  organizationNumber: '555555-5555'
};

let options = {
  url: 'https://app.seventime.se/api/1/customers',
  form: formData,
  headers: {
    "Client-Secret": clientSecret,
    "Content-Type": "x-www-form-urlencoded"
  }
};

request.post(options, function (error, response, body) {
  if (!error && response.statusCode === 200) {
    var data = JSON.parse(body);
    console.log(data);
  } else {
    console.error("ERROR! Unable to create customer: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "_id": "5bb26376c42fb99275000080",
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
  "__v": 0,
  "isActive": true
```

This endpoint creates a specific customer.

### HTTP Request

`POST https://app.seventime.se/api/1/customers/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
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
billingSettings     | Object | No | Contains attributes specific for billing. See below for details. 

    
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
    
# Users

## Get Users

```shell
curl "https://app.seventime.se/api/1/users" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/users/?";
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

[   
  { "_id": "5f48eb3e65d8ee4842c16ebb",
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
```

This endpoint retrieves users, a maximum of 100 users will be returned.

### HTTP Request

`GET https://app.seventime.se/api/1/users`

### Query Parameters

E.g. `https://app.seventime.se/api/1/users/?name=Tommy Hellström` 

Parameter | Default | Description
--------- | ------- | -----------
name |  | If specified, customers that match the parameter will be included.
customerNumber |  | If specified, customers that match the parameter will be included.
organizationNumber |  | If specified, customers that match the parameter will be included.
city |  | If specified, customers that match the parameter will be included.
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


<!--<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>-->
    
    
# Work orders

## Get Work orders


```shell
curl "https://app.seventime.se/api/1/workOrders" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/workOrders/?";
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
[
    {
        "_id": "5bae34dca878bd790d02065g",
        "workOrderNumber": 2901,
        "createdByUserName": "Tommy Hellström",
        "createdByUser": "5112826056d961c030000002",
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
        "__v": 0
    },
  {
    // ...
  }
]
```

This endpoint retrieves customers, a maximum of 100 work orders will be returned.

### HTTP Request

`GET https://app.seventime.se/api/1/workOrders`

### Query Parameters

E.g. `https://app.seventime.se/api/1/workOrders/?workOrderNumber=5555` 

Parameter | Default | Description
--------- | ------- | -----------
title |  | If specified, work orders that match the parameter will be included.
workOrderNumber |  | If specified, work orders that match the parameter will be included.
projectId |  | If specified, work orders that match the parameter will be included.
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


<!--<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>-->

## Get a Specific workOrder

```shell
curl "https://app.seventime.se/api/1/workOrders/5bae34dca878bd790d02065g" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/workOrders/5bae34dca878bd790d02065g";
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
    "createdByUser": "5112826056d961c030000002",
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
    "__v": 0,
    "relations": []
}
```

This endpoint retrieves a specific work order.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/workOrders/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the work order to retrieve

## Get work order types

```shell
curl "https://app.seventime.se/api/1/workOrderTypes/" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/workOrderTypes/";
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
[
    {
        "_id": "58263d936a17605a25020043",
        "isActive": true,
        "workOrderTypeName": "Extra",
        "__v": 0,
        "color": "f44336"
    },
    {
    // ...
    },

]
```

This endpoint retrieves work order types, a maximum of 100 types will be returned.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/workOrderTypes/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get work order tags

```shell
curl "https://app.seventime.se/api/1/workOrderTags/" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/workOrderTypes/";
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
[
    {
        "_id": "5df3a401f0690d1dbb3ec7bd",
        "tagName": "1",
        "color": "FAFAFA"
    },
    {
    // ...
    }

]
```

This endpoint retrieves work order tags, a maximum of 100 tags will be returned.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/workOrderTags/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending
  
  
## Create a Work order


```shell
  curl -X POST "https://app.seventime.se/api/1/workOrders/" \
  -H "Client-Secret: thisismysecretkey" \
  -d "name=Support&customer=571f61330c7f498a2d0001a4&createdByUser=5912626016d971c030916402" 
```

```javascript
let formData = {
  name: 'Support',
  customer: '571f61330c7f498a2d0001a4',
  createdByUser: '5912626016d971c030916402'
};

let options = {
  url: 'https://app.seventime.se/api/1/customers',
  form: formData,
  headers: {
    "Client-Secret": clientSecret,
    "Content-Type": "x-www-form-urlencoded"
  }
};

request.post(options, function (error, response, body) {
  if (!error && response.statusCode === 200) {
    var data = JSON.parse(body);
    console.log(data);
  } else {
    console.error("ERROR! Unable to create work order: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
    "title": "API test"
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
    // ...
    },
    "createdByUserName": "Lucas Hellström",
}
```

This endpoint creates a specific work order.

### HTTP Request

`POST https://app.seventime.se/api/1/workOrders/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
title               | String | Yes | Title of the work order
customer            | String | Yes | Customer id for the customer whom the work order should belong to
createdByUser       | String | Yes | Id of the user who created the work order
workOrderNumber     | String | No | Work order number. If specified it has to be unique otherwise an error will be returned. If not specified it will be set automatically.
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

Code | Status
--------- | ----------- 
RUNNING             | Running price
FIXED_PRICE         | Fixed price
ACCORDING_TO_QUOTE  | Price will be set according to quote



**Attributes for workAddress**

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
useOtherAddress             | Boolean | No | Should an alternative work address be used?
name                        | String | No | Used if useSeparateBillingAddress is true 
address                     | String | No | Used if useSeparateBillingAddress is true 
address2                    | String | No | Used if useSeparateBillingAddress is true
zipCode                     | String | No | Used if useSeparateBillingAddress is true
city                        | String | No | Used if useSeparateBillingAddress is true
country                     | String | No | Used if useSeparateBillingAddress is true, given as a country code (E.g. SE for Sweden)
phone                       | String | No | Used if useSeparateBillingAddress is true



**Attributes for DeductionItem** 
    
DeductionItem is used to distribute ROT / RUT work    
    
Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
    userName   | String| Yes | Full name of person 
    personalNumber   | String| Yes | Personal number
    distributionPercent   | Number | Yes | 1-100

    


