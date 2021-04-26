# Supplement Orders
## Get Supplement Orders

```shell
curl "https://app.seventime.se/api/2/supplementOrders/?project=5f924f4f533f102af78f95b6" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/supplementOrders/?project=5f924f4f533f102af78f95b6";
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

This endpoint retrieves supplement orders.

### HTTP Request

`GET https://app.seventime.se/api/2/supplementOrders/?project=5f924f4f533f102af78f95b6`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
project       |  | Id of the project that supplement orders will be retrieved from. This parameter is required
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
