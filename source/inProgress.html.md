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

## Update a Purchase Order

```shell
  curl -X PUT "https://app.seventime.se/api/2/purchaseOrders/" \
  -H "Client-Secret: thisismysecretkey" \
  -d "_id=5fca480e571eb873a64b97ec&modifiedByUser=51718241fdb708f37959127&paymentDays=10" 
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
    'Client-Secret': clientSecret,
    "Content-Type": "application/json",
    "Accept": 'application/json'
  }
};

request.post(options, function (error, response, body) {
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
  "__v": 0 
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

