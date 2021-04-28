# Supplier Invoices
## Get supplier invoices

```shell
curl "https://app.seventime.se/api/2/supplierInvoices/?limit=5&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/supplierInvoices/?limit=5&page=1";
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
      "_id": "5f62c5281715836a472254821",
      "isInvoiceable": false,
      "isInvoiced": false,
      "selfBillingTimeLogIds": [
        "5f5f6881241b6f02a6218724",
        "5f5f6881241b6f02a6879518"
      ],
      "selfBillingExpenseIds": [
        "5f5f8c6a5b2317286e285721",
        "5f5f8c6a5b2317286e698574"
      ],
      "invoiceItems": [
        {
          "_id": "5f60c501271935b912215879",
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
          "timeCategory": "5e81d33db3f1cb30a16489572",
          "categoryName": "Beredskap normal"
        },
        {
          // ...
        }
      ],
      "documents": [],
      "distributor": "5f48eb7105b8ed6934398752",
      "distributorName": "20200828",
      "yourReference": "Anna Andersson",
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
      "workOrder": "5f4df1793751c0916136489752",
      "workOrderTitle": "Återkommande 20200116 - 234556565656",
      "workOrderNumber": 4737,
      "project": null,
      "projectName": null,
      "supplementOrderId": null,
      "supplementOrderNumber": null,
      "customer": "5bb26376c42fb992716598742",
      "customerName": "Company",
      "department": null,
      "departmentName": "",
      "supplementOrder": false,
      "invoice": null,
      "invoiceNumber": "9316",
      "isSelfBillingInvoice": true,
      "selfBillingInvoiceStatus": 1,
      "exportedToEconomy": false,
      "selfBillingInvoice": "5f5f23fd716176146859257",
      "selfBillingInvoiceNumber": "24272",
      "footerText": "<table width=\"100%\"><tr><td style='vertical-align: top;'>Första</td><td style='vertical-align: top;'>Andra</td><td style='vertical-align: top;'>Tredje</td></tr></table>",
      "footerInfoText": "Text under..."
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves supplier invoices.

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
curl "https://app.seventime.se/api/2/supplierInvoices/5f62c528171548657d215a785" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/supplierInvoices/5f62c528171548657d215a785";
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
    "_id": "5f62c528171548657d215a785",
    "isInvoiceable": false,
    "isInvoiced": false,
    "selfBillingTimeLogIds": [
      "5f5f6881241b6f0221457985",
      "5f5f6881241b6f02a6364619"
    ],
    "selfBillingExpenseIds": [
      "5f5f8c6a5b2317286eb65482b",
      "5f5f8c6a5b2317286eb8d76b1"
    ],
    "invoiceItems": [
      {
        "_id": "5f60c501271935b9165897451",
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
        "timeCategory": "5e81d33db3f1cb30a2135842",
        "categoryName": "Beredskap normal"
      },
      {
        // ...
      }
    ],
    "documents": [],
    "distributor": "5f48eb7105b8ed6969875258",
    "distributorName": "20200828",
    "yourReference": "Anna Andersson",
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
    "workOrder": "5f4df1793751c0916134687952",
    "workOrderTitle": "Återkommande 20200116 - 234556565656",
    "workOrderNumber": 4737,
    "project": null,
    "projectName": null,
    "supplementOrderId": null,
    "supplementOrderNumber": null,
    "customer": "5bb26376c42fb91357498542",
    "customerName": "Company",
    "department": null,
    "departmentName": "",
    "supplementOrder": false,
    "invoice": null,
    "invoiceNumber": "9316",
    "isSelfBillingInvoice": true,
    "selfBillingInvoiceStatus": 1,
    "exportedToEconomy": false,
    "selfBillingInvoice": "5f5f23fd7161713589748562",
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
  -d '{"supplierInvoiceNumber":"9162","createdByUser":"5f48eb3e65d7e12574952d685","distributor":"5f6b2e6af24d5d69784521","totalAmountInclTax":"100000"}' 
```

```javascript
let jsonData = {
  supplierInvoiceNumber: 9162,
  createdByUser: '5f48eb3e65d7e12574952d685',
  distributor: '5f6b2e6af24d5d69784521',
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
  "_id": "5fd0619c739154975825",
  "invoiceItems": [],
  "documents": [],
  "supplierInvoiceLogEntries": [ 
    { 
      "_id": "5fdd142c621b21a10129",
      "logType": 1,
      "description": "",
      "user": "5f48eb3e65d7e12574952d685",
      "userName": "Anna Andersson",
      "logDate": "2020-12-09T12":43":51.516Z" 
    } 
  ],
  "markupPercent": 0,
  "distributor": "5f6b2e6af24d5d69784521",
  "distributorName": "Company AB",
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
  -d '{"_id":"5fd0619c739154975825","modifiedByUser":"5f48eb3e65d7ee4942c6859741","supplierInvoiceStatus":"7"}' 
```

```javascript
let jsonData = {
  _id: "5fd0619c739154975825",
  modifiedByUser: '5f48eb3e65d7ee4942c6859741',
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
  "_id": "5fd0619c739154975825",
  "invoiceItems": [],
  "documents": [],
  "supplierInvoiceLogEntries": [ 
    { 
      "_id": "5fdd142c621b649785231",
      "logType": 1,
      "description": "",
      "user": "5f48eb3e65d7ee897425862",
      "userName": "Anna Andersson",
      "logDate": "2020-12-09T12":43":51.516Z" 
    } 
  ],
  "markupPercent": 0,
  "distributor": "5f6b2e6af24d5df697845268",
  "distributorName": "Company AB",
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
"Supplier invoice updated: _id: 5fd0619c739154975825"
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
  -d '{"_id":"5fd0619c739154975825","deletedByUser":"51203146506d961c03649852317"}' 
```

```javascript
let jsonData = {
  _id: "5fd0619c739154975825",
  deletedByUser: "51203146506d961c03649852317"
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
  "_id": "5fd0619c739154975825",
  "supplierInvoiceNumber": "9162",
}
"Supplier invoice deleted: _id: 5fd0619c739154975825, number: 9162"
```

This endpoint deletes a supplier invoice

### HTTP Request

`DELETE https://app.seventime.se/api/2/supplierInvoices/`

### DELETE Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                 | String      | Yes | Id of the Supplier Invoice
