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

## Create a Supplier Invoice

```shell
  curl -X POST "https://app.seventime.se/api/1/supplierInvoices/" \
  -H "Client-Secret: thisismysecretkey" \
  -d "supplierInvoiceNumber=9162&createdByUser=5f48eb3e65d7ee4942c46eeb&distributor=5f6b2e6af24d5df55b69277&totalAmountInclTax=100000" 
```

```javascript
let formData = {
  supplierInvoiceNumber: 9162,
  createdByUser: '5f48eb3e65d7ee4942c46eeb',
  distributor: '5f6b2e6af24d5df55b69277',
  totalAmountInclTax: 100000
};

let options = {
  url: 'https://app.seventime.se/api/1/supplierInvoices',
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
  "_id": "5fd0619c7391b561bda0a7",
  "invoiceItems": [],
  "documents": [],
  "supplierInvoiceLogEntries": [ 
    { 
      "_id": "5fdd142c621b21a10129",
      "logType": 1,
      "description": "",
      "user": "5f48eb3e65d7ee4942c46eeb",
      "userName": "Tommy Hellström",
      "logDate": "2020-12-09T12":43":51.516Z" 
    } 
  ],
  "markupPercent": 0,
  "distributor": "5f6b2e6af24d5df55b69277",
  "distributorName": "Hellapps AB",
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
  "__v": 0 
}
```

This endpoint creates a supplier invoice

### HTTP Request

`POST https://app.seventime.se/api/1/supplierInvoices/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
supplierInvoiceNumber     | Number | Yes | Number of  the supplier invoice
createdByUser             | String | Yes | Id of the user who created the invoice
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
taxPercent            | Number | No  | Tax percent of the item. Only used if multipleTaxesOnRows is true. This must be 0, 6, 12 or 25% and if not specified, this will be set to 25%.
houseWorkTypeOfWork   | Number | No  | Type of work for the row. Used if invoiceType is 1 or 2. See below for details

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

