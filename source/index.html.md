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

This endpoint retrieves work orders, a maximum of 100 work orders will be returned.

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

## Get a Specific Work order

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

# Invoices

## Get Invoices


```shell
curl "https://app.seventime.se/api/1/invoices" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/invoices/?";
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
    "5fa2b550c289ea64821ea37b",
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
  "__v": 0,
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
```

This endpoint retrieves invoices, a maximum of 100 invoices will be returned.

### HTTP Request

`GET https://app.seventime.se/api/1/invoices`

### Query Parameters

E.g. `https://app.seventime.se/api/1/invoices/?invoiceNumber=24481`

Parameter | Default | Description
--------- | ------- | -----------
invoiceNumber |  | If specified, invoices that match the parameter will be included.
OCRNumber |  | If specified, invoices that match the parameter will be included.
customerNumber |  | If specified, invoices that match the parameter will be included.
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


<!--<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>-->

## Get a Specific Invoice

```shell
curl "https://app.seventime.se/api/1/invoices/5fab29b038bd334ab540ab53" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/invoices/5fae99b072aa334cb539ab73";
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
  "__v": 0,
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

```

This endpoint retrieves a specific invoice.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/invoice/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the invoice to retrieve

## Get Invoice Tags

```shell
curl "https://app.seventime.se/api/1/invoiceTags/" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/invoiceTags/";
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
    "_id": "5f742440d608b2201c3e7bab",
    "tagName": "Att granska",
    "color": "f44336"
  },
  {
  // ...
  }
]

```

This endpoint retrieves invoice tags, a maximum of 100 tags will be returned.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/invoiceTags/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Create an Invoice

```shell
  curl -X POST "https://app.seventime.se/api/1/invoices/" \
  -H "Client-Secret: thisismysecretkey" \
  -d "invoiceStatus=2&customer=571f21058d7f618a2d037165&createdByUser=51718241fdb708f37959127&language=EN" 
```

```javascript
let formData = {
  invoiceStatus: 'Support',
  customer: '571f21058d7f618a2d037165',
  createdByUser: '51718241fdb708f37959127',
  language: 'EN'
};

let options = {
  url: 'https://app.seventime.se/api/1/invoices',
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
       "user": [Object],
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
  "createdByUser":
   { 
   // ...
   },
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
```

This endpoint creates an invoice

### HTTP Request

`POST https://app.seventime.se/api/1/invoices/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
customer            | String | Yes | Customer id for the customer whom the invoice should belong to
createdByUser       | String | Yes | Id of the user who created the invoice
language            | String | Yes | Language of the invoice given as a language code, e.g. SV for Swedish
name                | String | No | Name of the invoice. If not specified, this will be set to 'Invoice' translated to the selected language
invoiceDate         | String | No | Invoice date. Has to be in the format YYYY-MM-DD. If not specified, this will be set to the current date
dueDate             | String | No | Due date. Has to be in the format YYYY-MM-DD. If not specified, this will be set to the invoice date + the default payment terms
project             | String | No | Id of the project of the invoice
marking             | String | No | Marking on the invoice
yourOrderNumber     | String | No | Your order number
contactPerson       | String | No | Id of the contact person. This contact person has to belong to the selected customer
ourReference        | Number | No | Id of the user that will be set as our reference.
deliveryAddress     | Object | No | Contains attributes for delivery address. See below for details
workOrder           | String | No | Id of the work order
resultUnit          | String | No | Id of the result unit
invoiceType         | Number | No | Type of invoice. 0 for Normal, 1 for ROT, 2 for RUT and 3 for construction
houseProperties     | Object | No* | *Required if invoiceType is set to 1 or 2. See below for details
priceList           | String | No | Id of the price list to be used. If specified, prices from the price list will be used for invoice items
multipleTaxesOnRows | Boolean | No | Should it be possible to set different taxes on invoice items? If set to false, all invoice items will use the same tax percent
taxPercent          | Number | No | Tax percent which will be used if multipleTaxesOnRows is set to false. This must be 0, 6, 12 or 25% and if not specified, this will be set to 25%.
currencyCode        | String | No | Currency code to be used on the invoice
currencyRate        | Number | No | Currency rate between SEK and the selected currency
notes               | String | No | Notes on the invoice
invoiceItems        | Array  | No | Array containing objects with invoice items. See below for details.
tags                | Array  | No | Array of tag ids


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

**Item types and type specified fields**

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

# Supplier invoices

## Get supplier invoices

```shell
curl "https://app.seventime.se/api/1/supplierInvoices/?" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/supplierInvoices/?";
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
    "__v": 0
  },
  {
  // ...
  }
]
```

This endpoint retrieves supplier invoices, a maximum of 100 supplier invoices will be returned.

### HTTP Request

`GET https://app.seventime.se/api/1/supplierInvoices`

### Query Parameters

E.g. `https://app.seventime.se/api/1/supplierInvoices/?supplierInvoiceNumber=9316`

Parameter | Default | Description
--------- | ------- | -----------
supplierInvoiceNumber    |  | If specified, supplier invoices that match the parameter will be included.
supplierInvoiceStatus    |  | If specified, supplier invoices that match the parameter will be included.
projectName              |  | If specified, supplier invoices that match the parameter will be included.
customerName             |  | If specified, supplier invoices that match the parameter will be included.
workOrderTitle           |  | If specified, supplier invoices that match the parameter will be included.
workOrderNumber          |  | If specified, supplier invoices that match the parameter will be included.
distributorName          |  | If specified, supplier invoices that match the parameter will be included.
fromInvoiceDate          |  | If specified, supplier invoices that match the parameter will be included.
toInvoiceDate            |  | If specified, supplier invoices that match the parameter will be included.
isInvoiceable            |  | If specified, supplier invoices that match the parameter will be included.
sortBy                   |  | If specified, a sort will be made on the specified parameter
sortDirection            |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

<!--<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>-->

## Get a Specific Supplier Invoice

```shell
curl "https://app.seventime.se/api/1/supplierInvoices/5f62c5281715836a4721b843" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/supplierInvoices/5f62c5281715836a4721b843";
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
  "__v": 0
}
```

This endpoint retrieves a specific supplier invoice.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/supplierInvoices/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the supplier invoice to retrieve




# Machines

## Get Machines


```shell
curl "https://app.seventime.se/api/1/machines" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/machines/?";
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
    "__v": 1,
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
```

This endpoint retrieves machines, a maximum of 100 machines will be returned.

### HTTP Request

`GET https://app.seventime.se/api/1/machines`

### Query Parameters

E.g. `https://app.seventime.se/api/1/machines/?machineNumber=21`

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


<!--<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>-->

## Get a Specific Machine

```shell
curl "https://app.seventime.se/api/1/machines/5a4bc02e40a13d7179005920" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/machines/5a4bc02e40a13d7179005920";
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
  "__v": 1,
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
```

This endpoint retrieves a specific machine.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/machine/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the machine to retrieve

## Get Machine Types

```shell
curl "https://app.seventime.se/api/1/machineTypes/" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/machineTypes/";
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
    "_id": "57e89fbae191f8ba2b28420",
    "name": "Fordon",
    "isActive": true,
    "createDate": "2017-10-19T12:50:50.361Z",
    "__v": 0
  },
  {
  // ...
  }
]

```

This endpoint retrieves machine types, a maximum of 100 types will be returned.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/machineTypes/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


# Machine Time Logs

## Get Machines Time Logs


```shell
curl "https://app.seventime.se/api/1/machineTimeLogs" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/machineTimeLogs/?";
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
    "__v": 0
  },
  {
  // ...
  }
]
```

This endpoint retrieves machines time logs, a maximum of 100 machine time logs will be returned.

### HTTP Request

`GET https://app.seventime.se/api/1/machineTimeLogs`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy           |  | If specified, a sort will be made on the specified parameter
sortDirection    |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


<!--<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>-->


## Get a Specific Machine Time Log

```shell
curl "https://app.seventime.se/api/1/machines/5a4bc02e40a13d7179005920" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/machines/5a4bc02e40a13d7179005920";
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
  "__v": 0
}
```

This endpoint retrieves a specific machine time log.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/machineTimeLog/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the machine time log to retrieve

# Time Logs

## Get Time Logs


```shell
curl "https://app.seventime.se/api/1/timeLogs" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/timeLogs/?";
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
    "_id": "514959f8733259db7591000c",
    "__v": 1,
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
```

This endpoint retrieves machines time logs, a maximum of 100 machine time logs will be returned.

### HTTP Request

`GET https://app.seventime.se/api/1/timeLogs`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
customerName       |  | If specified, time logs that match the parameter will be included.
projectName        |  | If specified, time logs that match the parameter will be included.
taskTitle          |  | If specified, time logs that match the parameter will be included.
categoryName       |  | If specified, time logs that match the parameter will be included.
workOrderTitle     |  | If specified, time logs that match the parameter will be included.
workOrderNumber    |  | If specified, time logs that match the parameter will be included.
sortBy             |  | If specified, a sort will be made on the specified parameter
sortDirection      |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


<!--<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>-->


## Get a Specific Time Log

```shell
curl "https://app.seventime.se/api/1/timeLogs/514959f8733259db7591000c" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/timeLogs/514959f8733259db7591000c";
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
  "__v": 1,
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

```

This endpoint retrieves a specific time log.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/timeLogs/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the time log to retrieve

## Get Time Categories


```shell
curl "https://app.seventime.se/api/1/timeCategories" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/timeCategories/?";
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
    "__v": 0,
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
```

This endpoint retrieves time categories, a maximum of 100 categories will be returned.

### HTTP Request

`GET https://app.seventime.se/api/1/timeCategories`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy             |  | If specified, a sort will be made on the specified parameter
sortDirection      |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


<!--<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>-->


## Get a Specific Time Category

```shell
curl "https://app.seventime.se/api/1/timeCategories/58cd3c4771b8a3c347041207" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/timeCategories/58cd3c4771b8a3c347041207";
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
  "__v": 0,
  "color": "FF9800",
  "isVacation": true,
  "presenceCode": "",
  "requirePreAttest": true,
  "isMachineTime": false
}
```

This endpoint retrieves a specific time category.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/timeCategories/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the time category to retrieve


## Create a Time Log

```shell
  curl -X POST "https://app.seventime.se/api/1/timeLogs/" \
  -H "Client-Secret: thisismysecretkey" \
  -d "user=51203146506d961c030791801&timestamp=2020-06-05 12:00&time=5"
```

```javascript
let formData = {
  user: '51203146506d961c030791801',
  timestamp: '2020-06-05 12:00',
  time: '5'
};

let options = {
  url: 'https://app.seventime.se/api/1/timeLogs',
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
  "__v": 0 
}
```

This endpoint creates a time log

### HTTP Request

`POST https://app.seventime.se/api/1/timeLogs/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
user                | String | Yes | User id 
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

# Expenses 

## Get Expenses

```shell
curl "https://app.seventime.se/api/1/expenses" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/expenses/?";
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
    "_id": "53ad291839f16d23a6414604d2",
    "__v": 0,
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
```

This endpoint retrieves expenses, a maximum of 100 expenses will be returned.

### HTTP Request

`GET https://app.seventime.se/api/1/expenses`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
name               |  | If specified, expenses that match the parameter will be included.
articleNumber      |  | If specified, expenses that match the parameter will be included.
customerName       |  | If specified, expenses that match the parameter will be included.
projectName        |  | If specified, expenses that match the parameter will be included.
distributorName    |  | If specified, expenses that match the parameter will be included.
sortBy             |  | If specified, a sort will be made on the specified parameter
sortDirection      |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

<!--<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>-->


## Get a Specific Expense

```shell
curl "https://app.seventime.se/api/1/expenses/53ad291839f16d23a6414604d2" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/expenses/53ad291839f16d23a6414604d2";
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
  "_id": "53ad291839f16d23a6414604d2",
  "__v": 0,
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
```

This endpoint retrieves a specific expense.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/expenses/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the expense to retrieve

## Get Expenses Items

```shell
curl "https://app.seventime.se/api/1/expenseItems" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/expenseItems/?";
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
    "__v": 0,
    "unitPriceInclTax": 369.48749999999995
  },
  {
  // ...
  }
]
```

This endpoint retrieves expense items, a maximum of 100 expense items will be returned.

### HTTP Request

`GET https://app.seventime.se/api/1/expenses`

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

<!--<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>-->


## Get a Specific Expense Item

```shell
curl "https://app.seventime.se/api/1/expenseItems/5de78aed1332719192362bed" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/expenseItems/5de78aed1332719192362bed";
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
  "__v": 0,
  "unitPriceInclTax": 369.48749999999995
}
```

This endpoint retrieves a specific expense item.

<!--
<aside class="warning">Inside HTML code blocks like this one, you can"t use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>
-->

### HTTP Request

`GET https://app.seventime.se/api/1/expenseItems/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the expense item to retrieve


## Create an Expense

```shell
  curl -X POST "https://app.seventime.se/api/1/expenses/" \
  -H "Client-Secret: thisismysecretkey" \
  -d "user=51203146506d961c030791801&expenseItem=5de78aed1332719192362bed"
```

```javascript
let formData = {
  user: '51203146506d961c030791801',
  expenseItem: '5de78aed1332719192362bed'
};

let options = {
  url: 'https://app.seventime.se/api/1/expenses',
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
  "__v": 0 
}

```

This endpoint creates an expense

### HTTP Request

`POST https://app.seventime.se/api/1/expenses/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
user                | String | Yes | User id
expenseItem         | String | Yes*| Id of the expense item. Required if freetext for articles is not activated 
name                | String | Yes*| Name of the article. Required if expenseItem is not specified. This will set the article to freetext and is only possible if the setting for this is enabled. 
workOrder           | String | No  | Id of the work order
customer            | String | No  | Id of the customer. If workOrder is specified, the customer from the work order will be used
project             | String | No  | Id of the project. If workOrder is specified, the project from the work order will be used
distributor         | String | No  | Id of the distributor
numberOfItems       | String | No  | Number of items
unit                | String | No  | Unit of the number of items
unitCost            | Number | No  | Cost per unit. If not specified, the cost on the expense item will be used
unitPrice           | Number | No  | Price per unit. If not specified, the price from the price list set on the customer will be used. If no price list is set, the price will be calculated from the cost and the 'Mark up on purchase price' on the customer. If 'Mark up on purchase price' is 0, the price will be set to the expense item price.
discountPercent     | Number | No  | Discount percent on the unit price
timestamp           | String | No  | Time stamp of expense
description         | String | No  | Description of the expense
isInvoiceable       | Boolean | No | Is the expense invoiceable?
doReimburse         | Boolean | No | Is the expense an own expense?

# Driver Journals
## Get Driver Journals

```shell
curl "https://app.seventime.se/api/1/driverJournals" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/driverJournals/?";
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
    "__v": 0
  },
  {
  // ...
  }
]
```

This endpoint retrieves driver journals, a maximum of 100 driver journals will be returned.

### HTTP Request

`GET https://app.seventime.se/api/1/driverJournals`

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
sortBy                      |  | If specified, a sort will be made on the specified parameter
sortDirection               |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

<!--<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>-->


## Get a Specific Driver Journal

```shell
curl "https://app.seventime.se/api/1/driverJournals/5613c0eabed82c732b67914b" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/driverJournals/5613c0eabed82c732b67914b";
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
  "__v": 0
}
```

This endpoint retrieves a specific driver journal.


### HTTP Request

`GET https://app.seventime.se/api/1/driverJournals/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the driver journal to retrieve

## Get Driver Journals

```shell
curl "https://app.seventime.se/api/1/driverJournalTypes" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/1/driverJournalTypes/?";
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
    "__v": 0,
    "salaryCode": "9172"
  },
  {
  // ...
  }
]
```

This endpoint retrieves driver journals types, a maximum of 100 driver journals types will be returned.

### HTTP Request

`GET https://app.seventime.se/api/1/driverJournalTypes`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy                      |  | If specified, a sort will be made on the specified parameter
sortDirection               |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


## Create an Driver Journal

```shell
  curl -X POST "https://app.seventime.se/api/1/driverJournals/" \
  -H "Client-Secret: thisismysecretkey" \
  -d "user=51203146506d961c030791801&expenseItem=5de78aed1332719192362bed"
```

```javascript
let formData = {
  user: '51203146506d961c030791801',
  expenseItem: '5de78aed1332719192362bed'
};

let options = {
  url: 'https://app.seventime.se/api/1/expenses',
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
  "__v": 0 
}

```

This endpoint creates an expense

### HTTP Request

`POST https://app.seventime.se/api/1/expenses/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
user                | String | Yes | User id
expenseItem         | String | Yes*| Id of the expense item. Required if freetext for articles is not activated
name                | String | Yes*| Name of the article. Required if expenseItem is not specified. This will set the article to freetext and is only possible if the setting for this is enabled.
workOrder           | String | No  | Id of the work order
customer            | String | No  | Id of the customer. If workOrder is specified, the customer from the work order will be used
project             | String | No  | Id of the project. If workOrder is specified, the project from the work order will be used
distributor         | String | No  | Id of the distributor
numberOfItems       | String | No  | Number of items
unit                | String | No  | Unit of the number of items
unitCost            | Number | No  | Cost per unit. If not specified, the cost on the expense item will be used
unitPrice           | Number | No  | Price per unit. If not specified, the price from the price list set on the customer will be used. If no price list is set, the price will be calculated from the cost and the 'Mark up on purchase price' on the customer. If 'Mark up on purchase price' is 0, the price will be set to the expense item price.
discountPercent     | Number | No  | Discount percent on the unit price
timestamp           | String | No  | Time stamp of expense
description         | String | No  | Description of the expense
isInvoiceable       | Boolean | No | Is the expense invoiceable?
doReimburse         | Boolean | No | Is the expense an own expense?



