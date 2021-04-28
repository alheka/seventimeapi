# Supplement Orders
## Get Supplement Orders

```shell
curl "https://app.seventime.se/api/2/supplementOrders/?project=5f924f4f533f102a4898752" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/supplementOrders/?project=5f924f4f533f102a4898752";
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
      "_id": "5ba5619ad77ca8741398752",
      "title": "Discount",
      "description": "",
      "headerText": "",
      "supplementOrderNumber": 1,
      "supplementOrderType": 1,
      "createdByUser": "5f48eb3e65d7ee46897851326584",
      "createdByUserName": "Anna Andersson",
      "customer": "5bb26376c42fb99469875216",
      "customerName": "Company AB",
      "project": "5f924f4f5335794216587",
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
      "publicLink": "B2R8LWK5bakdBtTuWv7",
      "footerText": "<table width=\"100%\"><tr><td style='vertical-align: top;'></td><td style='vertical-align: top;'></td><td style='vertical-align: top;'></td></tr></table>",
      "deviations": [],
      "supplementOrderLogEntries": [
        {
          "logType": 1,
          "description": "",
          "user": "5f48eb3e65d7ee4945798521",
          "userName": "Anna Andersson",
          "_id": "5ba5619ad77ca8791257284",
          "logDate": "2018-09-25T07:12:46.369Z"
        },
        {
        // ...
        }
      ],
      "documents": [],
      "workOrderIds": [
        "5bae34dca878bd79245168547"
      ],
      "invoiceIds": [
        "5f62c5281715836a49878521",
        "524f29251c11237389745654"
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
          "expenseItem": "5266af51d887512654897852",
          "expenseItemName": "Company - 5 användare - #2",
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

`GET https://app.seventime.se/api/2/supplementOrders/?project=5f924f4f533f102a4898752`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
project       |  | Id of the project that supplement orders will be retrieved from. This parameter is required
sortBy        |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get a specific Supplement Order

```shell
curl "https://app.seventime.se/api/2/supplementOrders/5ba5619ad77ca879794258752" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/supplementOrders/5ba5619ad77ca879794258752";
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
      "_id": "5ba5619ad77ca879794258752",
      "title": "Discount",
      "description": "",
      "headerText": "",
      "supplementOrderNumber": 1,
      "supplementOrderType": 1,
      "createdByUser": "5f48eb3e65d7ee4942659852",
      "createdByUserName": "Anna Andersson",
      "customer": "5bb26376c42fb98755218",
      "customerName": "Company AB",
      "project": "5f924f4f533f102af65897421",
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
      "publicLink": "B2R8LWK5bakDbUTDnzX",
      "footerText": "<table width=\"100%\"><tr><td style='vertical-align: top;'></td><td style='vertical-align: top;'></td><td style='vertical-align: top;'></td></tr></table>",
      "deviations": [],
      "supplementOrderLogEntries": [
        {
          "logType": 1,
          "description": "",
          "user": "5f48eb3e65d7ee49489741358",
          "userName": "Anna Andersson",
          "_id": "5ba5619ad77ca8791257284",
          "logDate": "2018-09-25T07:12:46.369Z"
        },
        {
        // ...
        }
      ],
      "documents": [],
      "workOrderIds": [
        "5bae34dca878bd7909852125"
      ],
      "invoiceIds": [
        "5f62c5281715836a42185872",
        "524f29251c112373a3215652"
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
          "expenseItem": "5266af51d887512879216458",
          "expenseItemName": "Company - 5 användare - #2",
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
