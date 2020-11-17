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
    
# Contact Persons

## Get Contact Persons


```shell
curl "https://app.seventime.se/api/1/contactPersons" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/contactPersons/?customerId=5bb26376c42fb99275000080";
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
    "__v": 0
  },
  {
  // ...
  }
]
```

This endpoint retrieves contact persons, a maximum of 100 contact persons will be returned.

### HTTP Request

`GET https://app.seventime.se/api/1/contactPersons`

### Query Parameters

E.g. `https://app.seventime.se/api/1/contactPersons/?customerId=5bb26376c42fb99275000080` 

Parameter | Default | Description
--------- | ------- | -----------
customerId | | The id of the customer which the contact persons belong to. This field is required
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get a Specific Contact Person

```shell
curl "https://app.seventime.se/api/1/contactPersons/5fb7bcd0ab7bb01d4d798762" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/contactPersons/5fb7bcd0ab7bb01d4d798762";
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
    "__v": 0
}
```

This endpoint retrieves a contact persons.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/contactPersons/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the contact person to retrieve    
    
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
  { "_id": "5f48eb3e65d7ee4942c46eeb",
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
name |  | If specified, users that match the parameter will be included.
personNumber |  | If specified, users that match the parameter will be included.
department |  | If specified, users that match the parameter will be included.
userRole |  | If specified, users that match the parameter will be included.
isActive |  | If specified, users that match the parameter will be included. This must be a boolean
isActivated |  | If specified, users that match the parameter will be included. This must be a boolean
defaultSalaryType |  | If specified, users that match the parameter will be included. 
userSkills |  | If specified, users that match the parameter will be included.
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


<!--<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>-->

## Get a Specific User

```shell
curl "https://app.seventime.se/api/1/users/5f48eb3e65d7ee4942c46eeb" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/users/5f48eb3e65d7ee4942c46eeb";
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
  "_id": "5112826056d961c030000002",
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
```

This endpoint retrieves a specific user

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/users/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the user to retrieve

## Get User Roles

```shell
curl "https://app.seventime.se/api/1/userRoles/" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/userRoles/";
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
        "userRoleId": 1,
        "userRoleName": "Administratör"
    },
    {
    // ...
    }
]
```

This endpoint retrieves user roles, a maximum of 100 user roles will be returned.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/userRoles/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get User Salary types

```shell
curl "https://app.seventime.se/api/1/defaultSalaryTypes/" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/defaultSalaryTypes/";
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
        "_id": "5834419c7a27db6932000052",
        "name": "Övertid",
        "description": "",
        "code": "123",
        "isAbsenceTimeType": false,
        "isRuleType": false,
        "absenceTimeCategory": null,
        "absenceTimeCategoryName": "",
        "__v": 0,
        "unitType": "1",
        "canBeRegistered": true,
        "salaryAmount": 0,
        "typeInSalarySystem": 10
    },
    {
    // ...
    }
]
```

This endpoint retrieves user salary types, a maximum of 100 salary types will be returned.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/defaultSalaryTypes/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get User Skills

```shell
curl "https://app.seventime.se/api/1/userSkills/" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/userSkills/";
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
        "_id": "59f9d1c53ffd5f932a000067",
        "systemAccount": "5112826056d961c030000001",
        "skillTitle": "Höga arbeten",
        "__v": 0,
        "requireEducations": [
            "5a54ea1f7a7fe3c26200006e"
        ]
    },
    {
    // ...
    }
]
```

This endpoint retrieves user skills, a maximum of 100 user skills will be returned.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/userSkills/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Create User

```shell
  curl -X POST "https://app.seventime.se/api/1/users/" \
  -H "Client-Secret: thisismysecretkey" \
  -d "firstName=Tommy&lastName=Hellström&email=tommy@nummer7.se&userName=TommyH&userRolesId=1" 
```

```javascript
let formData = {
  firstName: 'Tommy',
  lastName: 'Hellström',
  email: 'tommy@nummer7.se',
  userName: 'TommyH',
  userRoleId: 1,
};

let options = {
  url: 'https://app.seventime.se/api/1/users',
  form: formData,
  json: true,
  headers: {
    'Client-Secret': clientSecret,
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

`POST https://app.seventime.se/api/1/workOrders/`

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
language           | String   | No  | Language of the user as a country code (e.g SV for Swedish). If not specified, this will we set to SV.


# Departments

## Get Departments


```shell
curl "https://app.seventime.se/api/1/departments" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/departments/?";
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
    "_id": "59d05abdc471b72e4901079",
    "name": "Utveckling",
    "departmentNumber": "2",
    "isActive": true,
    "managerIds": [],
    "__v": 0
  },
  {
    // ...
  }
]
```

This endpoint retrieves departments, a maximum of 100 departments will be returned.

### HTTP Request

`GET https://app.seventime.se/api/1/departments`

### Query Parameters

E.g. `https://app.seventime.se/api/1/departments/?` 

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get a Specific Department

```shell
curl "https://app.seventime.se/api/1/departments/59d05abdc471b72e4901079" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/departments/59d05abdc471b72e4901079";
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
    "managerIds": [],
    "_id": "59d05abdc471b72e4901079",
    "name": "Utveckling",
    "departmentNumber": "2",
    "isActive": true,
    "__v": 0
}
```

This endpoint retrieves a specific department.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/departments/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the department to retrieve
    

# Projects

## Get Projects


```shell
curl "https://app.seventime.se/api/1/projects" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/projects/?";
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
      "__v": 0
  }, 
  {
  // ...
  }
]
```

This endpoint retrieves projects, a maximum of 100 projects will be returned.

### HTTP Request

`GET https://app.seventime.se/api/1/projects`

### Query Parameters

E.g. `https://app.seventime.se/api/1/projects/?projectNumber=3314` 

Parameter | Default | Description
--------- | ------- | -----------
name |  | If specified, projects that match the parameter will be included.
projectNumber |  | If specified, projects that match the parameter will be included.
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


<!--<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>-->

## Get a Specific project

```shell
curl "https://app.seventime.se/api/1/projects/5f924f4f533f102af78f95b6" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/projects/5f924f4f533f102af78f95b6";
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
    "__v": 0
}
```

This endpoint retrieves a specific project.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/projects/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the project to retrieve

## Get Project statuses

```shell
curl "https://app.seventime.se/api/1/projectStatuses/" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/projectStatuses/";
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
    "_id": "5c8639c4704957d88b9894b1",
    "statusName": "Avslutad",
    "color": "468847",
    "inProgressStatus": false,
    "closedStatus": true,
    "isActive": true
  },
  {
  // ...
  },

]
```

This endpoint retrieves project statuses, a maximum of 100 statuses will be returned.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/projectStatuses/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get Project types

```shell
curl "https://app.seventime.se/api/1/projectTypes/" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/projectTypes/";
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
    "_id": "5b276a908e0273b743607182",
    "projectTypeName": "Dev",
    "isActive": true,
    "__v": 0
  },
  {
  // ...
  },

]
```

This endpoint retrieves project types, a maximum of 100 types will be returned.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/projectTypes/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get Project tags

```shell
curl "https://app.seventime.se/api/1/projectTags/" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/projectTags/";
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
      "_id": "5fb2c736deb93b2713515684",
      "tagName": "Viktigt",
      "color": "673ab7"
  },
  {
  // ...
  },

]
```

This endpoint retrieves project tags, a maximum of 100 tags will be returned.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/projectTags/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Create a Project


```shell
  curl -X POST "https://app.seventime.se/api/1/projects/" \
  -H "Client-Secret: thisismysecretkey" \
  -d "name=App development" 
```

```javascript
const formData = {
  name: 'App development',
};

const options = {
  url: 'https://app.seventime.se/api/1/projects',
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
    console.error("ERROR! Unable to project: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
    budget: { benefits: [], costs: [] },
    budgetCalculation: { invoiceItems: [] },
    permissions: { permUsers: [], permRoles: [], permDepartments: [] },
    _id: '5fb3c92dd5472a243e9caa3b',
    tags: [],
    createdDate: '2020-11-17T12:59:25.109Z',
    modifiedDate: '2020-11-17T12:59:25.109Z',
    documents: [],
    timeCategoryItems: [],
    expenseItemItems: [],
    timeLogRegistrationMethods: [],
    projectResources: [],
    checkLists: [],
    comments: [],
    customFields: [],
    systemAccount: '5112826056d961c030000001',
    name: 'API test 4',
    projectNumber: '12345786' 
}
```

This endpoint creates a project.

### HTTP Request

`POST https://app.seventime.se/api/1/projects/name=App development`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
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

let url = "https://app.seventime.se/api/1/workOrderTags/";
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
  
## Get Work order statuses 

```shell
curl "https://app.seventime.se/api/1/workOrderStatuses/" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/workOrderStatuses/";
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
```

This endpoint retrieves work order statuses, a maximum of 100 statuses will be returned.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/workOrderStatuses/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Create a Work order


```shell
  curl -X POST "https://app.seventime.se/api/1/workOrders/" \
  -H "Client-Secret: thisismysecretkey" \
  -d "title=Support&customer=571f61330c7f498a2d0001a4&createdByUser=5912626016d971c030916402" 
```

```javascript
let formData = {
  title: 'Support',
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

# Price lists

## Get price lists

```shell
curl "https://app.seventime.se/api/1/priceLists" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/priceLists";
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
    "_id": "58c1504a658fb5911d018f5f",
    "name": "Grosslistan",
    "isActive": true,
    "__v": 0
  },
  {
  // ...
  }
]
```

This endpoint retrieves price lists, a maximum of 100 price lists will be returned.

### HTTP Request

`GET https://app.seventime.se/api/1/projects`

### Query Parameters

E.g. `https://app.seventime.se/api/1/projects/?projectNumber=3314`

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


<!--<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>-->



