# Purchase Orders
## Get Purchase Orders

```shell
curl "https://app.seventime.se/api/2/purchaseOrders/?limit=2&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/purchaseOrders/?limit=2&page=1";
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

This endpoint retrieves purchase orders.

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
  -d '{"_id":"5fca480e571eb873a64b97ec","deletedByUser":"51203146506d961c030791801"}' 
```

```javascript
let jsonData = {
  _id: '5fca480e571eb873a64b97ec',
  deletedByUser: '51203146506d961c030791801'
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
