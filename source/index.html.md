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
  url: url
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
  url: url
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

`POST https://app.seventime.se/api/1/customers/<_id>`

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

    


