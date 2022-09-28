# Customers

## Get Customers


```shell
curl "https://app.seventime.se/api/2/customers/?limit=10&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/customers/?limit=10&page=1";
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
      "_id": "571f61330c7f498a2d5812",
      "customerNumber": "733352",
      "vatNumber": "SE555708197354",
      "organizationNumber": "555555-5555",
      "email": "email@company.com",
      "phone": "1234-123456",
      "city": "Stockholm",
      "zipCode": "123 45",
      "address": "Östra Gatan 129",
      "name": "Anna Andersson",
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
            "userName": "Anna Andersson",
            "personalNumber": "555555-5555",
            "distributionPercent": 100,
            "_id": "5bb2683d3a0f154899"
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

This endpoint retrieves customers.

### HTTP Request

`GET https://app.seventime.se/api/2/customers`

### Query Parameters

E.g. `https://app.seventime.se/api/2/customers/?limit=10&page=1&organizationNumber=555555-5555`

Parameter | Default | Description
--------- | ------- | -----------
name                |  | If specified, customers that match the parameter will be included.
customerNumber      |  | If specified, customers that match the parameter will be included.
organizationNumber  |  | If specified, customers that match the parameter will be included.
city                |  | If specified, customers that match the parameter will be included.
lastModified        |  | If specified, customers that has been modified since the specified timestamp will be included. Accepted formats: 'YYYY-MM-HH HH:MM', 'YYYY-MM-HH HH:MM:SS', 'YYYY-MM-HHTHH:MM', 'YYYY-MM-HHTHH:MM:SS'
sortBy              |  | If specified, a sort will be made on the specified parameter
sortDirection       |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


## Get a specific Customer

```shell
curl "https://app.seventime.se/api/2/customers/571f61330c7f4124592b" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/customers/571f61330c7f4124592b";
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
    "_id": "571f61330c7f498a364892",
    "customerNumber": "733352",
    "vatNumber": "SE555702476792",
    "organizationNumber": "555555-5555",
    "email": "email@company.com",
    "phone": "1234-123456",
    "city": "Stockholm",
    "zipCode": "123 45",
    "address": "Östra Gatan 129",
    "name": "Anna Andersson",
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
          "userName": "Anna Andersson",
          "personalNumber": "555555-5555",
          "distributionPercent": 100,
          "_id": "5bb2683d3a0fdb85133"
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
Curl -X POST "https://app.seventime.se/api/2/customers/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"createdByUser":"5f48eb3e65d7ee8984354b","name":"Anna Andersson","address":"Östra Gatan 129","zipCode":"123 45","city":Stockholm","phone":1234-123456","email":"email@company.com","organizationNumber":"555555-5555"}'
```

```javascript
let jsonData = {
  createdByUser: '5f48eb3e65d7ee8984354b',
  name: 'Anna Andersson',
  address: 'Östra Gatan 129',
  zipCode: '123 45',
  city: 'Stockholm',
  phone: '1234-123456',
  email: 'email@company.com',
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
  "_id": "571f61330c7f498a4712448b",
  "customerNumber": "733352",
  "organizationNumber": "555555-5555",
  "email": "email@company.com",
  "phone": "1234-123456",
  "city": "Stockholm",
  "zipCode": "123 45",
  "address": "Östra Gatan 129",
  "name": "Anna Andersson",
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
deliveryAddress     | Object | No | Contains attributes specific for delivery. See below for details.
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
  -d '{"_id":"571f61330c7f498a4712448b","modifiedByUser":"5f48eb3e65d7ee49649eeb","name":"Company AB","customerNumber":"733352"}' 
```

```javascript
let jsonData = {
  _id: '571f61330c7f498a4712448b',
  modifiedByUser: '5f48eb3e65d7ee49649eeb',
  name: 'Company AB',
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
  "_id": "571f61330c7f498a4712448b",
  "customerNumber": "733352",
  "organizationNumber": "555555-5555",
  "email": "email@company.com",
  "phone": "1234-123456",
  "city": "Stockholm",
  "zipCode": "123 45",
  "address": "Östra Gatan 129",
  "name": "Company AB",
  "documents": [],
  "billingSettings": {
    "deductionDistribution": []
  },
  "modifiedDate": "2018-10-01T18:12:06.025Z",
  "createdDate": "2018-10-01T18:12:06.025Z",
  "isActive": true  
}
"Customer updated: Company AB, _id: 571f61330c7f498a4712448b"
```

This endpoint updates a customer.

### HTTP Request

`PUT https://app.seventime.se/api/2/customers/`

### PUT Parameters
The table below shows the required fields. Other available fields can be found in the section 'Create a Customer'.


Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                 | String | Yes | Id of the customer
modifiedByUser      | String | Yes | Id of the user who updated the customer

<!---
## Delete a Customer

```shell
curl -X DELETE "https://app.seventime.se/api/2/customers/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"571f61330c7f498a4712448b","deletedByUser":"5f48eb3e65d7ee4942c446872"}' 
```

```javascript
let jsonData = {
  _id: '571f61330c7f498a4712448b',
  deletedByUser: '5f48eb3e65d7ee4942c446872'
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
  "_id": "571f61330c7f498a4712448b",
  "customerNumber": "733352",
  "name": "Company AB",
}
"Customer deleted: Company AB, _id: 571f61330c7f498a4712448b"
```

This endpoint deletes a specific customer.

### HTTP Request

`DELETE https://app.seventime.se/api/2/customers/`

### DELETE Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                 | String | Yes | Id of the customer
deletedByUser       | String | Yes | Id of the user who deleted the customer
-->
