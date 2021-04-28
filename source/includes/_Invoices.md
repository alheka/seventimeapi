# Invoices

## Get Invoices


```shell
curl "https://app.seventime.se/api/2/invoices/?limit=3&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/invoices/?limit=3&page=1";
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
    "totalResources": 1987,
    "totalPages": 663,
    "currentPage": 9
  },
  "data": [
    {
      "_id": "5fab29b038bd334ab5402446",
      "deliveryAddress": {
        "name": "Kontoret",
        "address": "Östra Gatan 129",
        "address2": "Västra Gatan 921",
        "zipCode": "12345",
        "city": "Stockholm",
        "country": "SE",
        "phone": "1234-567890"
      },
      "houseProperties": {
        "typeOfProperty": 1,
        "propertyDescription": "property description",
        "housingSocietyNumber": "",
        "apartmentNumber": "",
        "maxDeductionAmount": 100000,
        "personalNumber": "",
        "deductionDistribution": [
          {
            "_id": "5fae99b072aa334cb533648",
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
        "5fa2b550c289ea61785952",
        // ...
      ],
      "tags": [
        "5f742440d608b220152b1549",
        "5f74243ad608b22058126b12"
      ],
      "createDate": "2020-11-13T14:35:28.797Z",
      "invoiceItems": [
        {
          "_id": "5fae99b072aa334cb52449682",
          "createDate": "2020-11-13T14:35:28.795Z",
          "houseWorkTypeOfWork": 1,
          "name": "**Skivhantel i Gummi 10 Kg****",
          "description": "Skivhantel av järn",
          "expenseItem": "5de78ae9bb1356246889512",
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
          "_id": "5fae99b072aa3667942258",
          "logDate": "2020-11-13T14:35:28.797Z",
          "logType": 1,
          "description": "",
          "user": "51714655fbb708f54975368",
          "userName": "Anna Andersson",
          "additionalData": ""
        },
        {
          // ...
        }
      ],
      "invoiceName": "Invoice",
      "marking": "marking",
      "yourOrderNumber": "12345",
      "notes": "invoice notes",
      "taxPercent": 12,
      "invoiceStatus": 2,
      "invoiceDate": "2020-11-04T23:00:00.000Z",
      "createdByUser": "51714655fbb708f37966632571",
      "createdByUserName": "Anna Andersson",
      "customer": "5cc05b6a4e595e68466411b",
      "customerName": "Company AB",
      "dueDate": "2020-12-04T23:00:00.000Z",
      "language": "EN",
      "project": "5b20cce1d59a902e28489125b",
      "projectName": "Blåsippan",
      "contactPerson": "5af95e6b1e557892234",
      "contactPersonName": "Anna Andersson",
      "ourReference": "518ff209d5a658451412",
      "ourReferenceName": "Anna Andersson",
      "workOrder": "5fa2b550c289ea96544921",
      "workOrderNumber": "4843",
      "invoiceType": 1,
      "resultUnit": "5784ff52fc71ce243b889d22482",
      "resultUnitName": "Kontor Nord",
      "priceList": "57bc187159a73f31230b5186472d25",
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
      "archived": false,
      "archivedDate": null,
      "creditForInvoice": null,
      "creditForInvoiceNumber": "",
      "creditInvoice": null,
      "creditInvoiceNumber": "",
      "currencyRate": 1,
      "customerAddress": "Östra Gatan 129<br>123 45 Stockholm",
      "customerEmail": "email@company.com",
      "customerNumber": "3028",
      "customerOrgNo": "",
      "customerVAT": "",
      "description": null,
      "discountInPercent": 0,
      "exportedToEconomy": false,
      "footerInfoText": null,
      "footerText": "<table width=\"100%\"><tr><td style='vertical-align: top;'><div><div><span style=\"font-size: 11px;\"></span></div></div></td><td style='vertical-align: top;'><div><span style=\"font-size: 11px;\">Efter förfallodagen debiteras dröjsmålsränta: 13.0%</span></div><div><br></div></td><td style='vertical-align: top;'><span style=\"font-size: 11px;\">Äganderättsförbehåll tills full likvid erlagts</span><span style=\"font-size: 11px;\">.</span><br></td><td style='vertical-align: top;'><div><span style=\"font-size: 11px;\">Godkänd för F-skatt</span></div><div><br></div></td></tr></table>",
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
}
```

This endpoint retrieves invoices.

### HTTP Request

`GET https://app.seventime.se/api/2/invoices`

### Query Parameters

E.g. `https://app.seventime.se/api/2/invoices/?invoiceNumber=24481`

Parameter | Default | Description
--------- | ------- | -----------
invoiceNumber       |  | If specified, invoices that match the parameter will be included.
OCRNumber           |  | If specified, invoices that match the parameter will be included.
customerNumber      |  | If specified, invoices that match the parameter will be included.
fromInvoiceDate     |  | If specified, invoices with invoice date after or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
toInvoiceDate       |  | If specified, invoices with invoice date before or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
fromDueDate         |  | If specified, invoices with due date after or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
toDueDate           |  | If specified, invoices with due date before or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
sortBy              |  | If specified, a sort will be made on the specified parameter
sortDirection       |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending




## Get a specific Invoice

```shell
curl "https://app.seventime.se/api/2/invoices/5fab29b038b7789542665" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/invoices/5fab29b038b7789542665";
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
      "name": "Kontoret",
      "address": "Östra Gatan 129",
      "address2": "Västra Gatan 921",
      "zipCode": "12345",
      "city": "Stockholm",
      "country": "SE",
      "phone": "12345-6798"
    },
    "houseProperties": {
      "typeOfProperty": 1,
      "propertyDescription": "property description",
      "housingSocietyNumber": "",
      "apartmentNumber": "",
      "maxDeductionAmount": 100000,
      "personalNumber": "",
      "deductionDistribution": [
        {
          "_id": "5fae99b072aa3548648942372",
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
      "5fa2b550c289ea55486219"
    ],
    "externalSystemExport": [],
    "tags": [
      "5f742440d608b22078942bd66",
      "5f74243ad608b25489256488b"
    ],
    "_id": "5fae99b072aa334cb5a5979425d",
    "createDate": "2020-11-13T14:35:28.797Z",
    "invoiceItems": [
      {
        "createDate": "2020-11-13T14:35:28.795Z",
        "_id": "5fae99b072aa334cb5399723547b",
        "houseWorkTypeOfWork": 1,
        "name": "**Skivhantel i Gummi 10 Kg****",
        "description": "Skivhantel av järn",
        "expenseItem": "5de78ae9bb1356594897615",
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
        "_id": "5fae99b072aa334c64897216",
        "logType": 1,
        "description": "",
        "user": "51714655fbb708f3647823159",
        "userName": "Anna Andersson",
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
        "_id": "5fb5217e4ea82f6477123584dd",
        "fieldId": "5f67af2796bce97845216892",
        "value": {
          "distributorId": null,
          "distributorName": ""
        }
      }
    ],
    "invoiceName": "Invoice",
    "marking": "marking",
    "yourOrderNumber": "12345",
    "notes": "invoice notes",
    "taxPercent": 12,
    "invoiceStatus": 2,
    "invoiceDate": "2020-11-04T23:00:00.000Z",
    "createdByUser": "51714655fbb708f3754578228",
    "createdByUserName": "Anna Andersson",
    "customer": "5cc05b6a4e595e6854976137451b",
    "customerName": "Company AB",
    "dueDate": "2020-12-04T23:00:00.000Z",
    "language": "EN",
    "project": "5b20cce1d59a979134679582",
    "projectName": "Blåsippan",
    "contactPerson": "5af95e6b1e56d12235489761954",
    "contactPersonName": "Anna Andersson",
    "ourReference": "518ff209d5af91647923578",
    "ourReferenceName": "Anna Andersson",
    "workOrder": "5fa2b550c289ea64845842b",
    "workOrderNumber": "4843",
    "invoiceType": 1,
    "resultUnit": "5784ff52fc71ce243d1354892",
    "resultUnitName": "Kontor Nord",
    "priceList": "57bc187159a73f3164915be",
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
    "archived": false,
    "archivedDate": null,
    "creditForInvoice": null,
    "creditForInvoiceNumber": "",
    "creditInvoice": null,
    "creditInvoiceNumber": "",
    "currencyRate": 1,
    "customerAddress": "Östra Gatan 129<br>123 45 Stockholm",
    "customerEmail": "email@company.com",
    "customerNumber": "3028",
    "customerOrgNo": "",
    "customerVAT": "",
    "description": null,
    "discountInPercent": 0,
    "exportedToEconomy": false,
    "footerInfoText": null,
    "footerText": "<table width=\"100%\"><tr><td style='vertical-align: top;'><div><div><span style=\"font-size: 11px;\"></span></div></div></td><td style='vertical-align: top;'><div><span style=\"font-size: 11px;\">Efter förfallodagen debiteras dröjsmålsränta: 13.0%</span></div><div><br></div></td><td style='vertical-align: top;'><span style=\"font-size: 11px;\">Äganderättsförbehåll tills full likvid erlagts</span><span style=\"font-size: 11px;\">.</span><br></td><td style='vertical-align: top;'><div><span style=\"font-size: 11px;\">Godkänd för F-skatt</span></div><div><br></div></td></tr></table>",
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
}
```

This endpoint retrieves a specific invoice.



### HTTP Request

`GET https://app.seventime.se/api/2/invoices/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the invoice to retrieve

## Get Invoice Tags

```shell
curl "https://app.seventime.se/api/2/invoiceTags/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/invoiceTags/";
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
  "data": [
    {
      "_id": "5f742440d608b22448b22791",
      "tagName": "Att granska",
      "color": "f44336"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves invoice tags.



### HTTP Request

`GET https://app.seventime.se/api/2/invoiceTags/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy          |  | If specified, a sort will be made on the specified parameter
sortDirection   |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Create an Invoice
```shell
curl -X POST "https://app.seventime.se/api/2/invoices/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"invoiceStatus":"2","customer":"571f21058d7f612467981357165","createdByUser":"51718241fdb7084835249227","language":"EN"}' 
```

```javascript
let jsonData = {
  invoiceStatus: 'Support',
  customer: '571f21058d7f612467981357165',
  createdByUser: '51718241fdb7084835249227',
  language: 'EN'
};

let options = {
  url: 'https://app.seventime.se/api/2/invoices',
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
    console.log("Invoice created: _id: " + body._id);
  } else {
    console.error("ERROR! Unable to create invoice: " + error);
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
  "_id": "5fb64449b0cc951024822167",
  "createDate": "2020-11-19T10:09:13.039Z",
  "invoiceItems": [],
  "documents": [],
  "invoiceLogEntries":
   [ 
    { "_id": "5fb64449b0cc95679815",
       "logType": 1,
       "description": "",
       "user": "5f48eb3e65d7479134682",
       "userName": "Anna Andersson",
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
  "invoiceName": "Invoice",
  "marking": "",
  "yourOrderNumber": "",
  "notes": "",
  "taxPercent": 25,
  "invoiceStatus": 2,
  "invoiceDate": "2020-11-19T10:09:13.033Z",
  "createdByUser": "51718241fdb7084835249227",
  "createdByUserName": "Anna Andersson",
  "customer": "571f21058d7f612467981357165",
  "customerName": "Company",
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
"Invoice created: _id: 5fb64449b0cc951024822167"
```

This endpoint creates an invoice

### HTTP Request

`POST https://app.seventime.se/api/2/invoices/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
customer            | String | Yes | Customer id for the customer who the invoice should belong to
createdByUser       | String | Yes | Id of the user who created the invoice
language            | String | Yes | Language of the invoice given as a language code, e.g. SV for Swedish
name                | String | No | Name of the invoice. If not specified, this will be set to 'Invoice' translated to the selected language
invoiceDate         | String | No | Invoice date. Has to be in the format YYYY-MM-DD. If not specified, this will be set to the current date
dueDate             | String | No | Due date. Has to be in the format YYYY-MM-DD. If not specified, this will be set to the invoice date + the default payment terms
project             | String | No | Id of the project of the invoice
marking             | String | No | Marking on the invoice
yourOrderNumber     | String | No | Your order number
invoiceStatus       | Number | No | Status of the invoice. 1 for 'Draft' and 2 for 'Sent'
contactPerson       | String | No | Id of the contact person. This contact person has to belong to the selected customer
ourReference        | Number | No | Id of the user that will be set as our reference.
deliveryAddress     | Object | No | Contains attributes for delivery address. See below for details
workOrder           | String | No | Id of the work order
resultUnit          | String | No | Id of the result unit
invoiceType         | Number | No | Type of invoice. 0 for Normal, 1 for ROT, 2 for RUT and 3 for construction
houseProperties     | Object | No* | *Required if invoiceType is set to 1 or 2. See below for details
priceList           | String | No | Id of the price list to be used. If specified, prices from the price list will be used for invoice items
multipleTaxesOnRows | Boolean | No | Should it be possible to set different taxes on invoice items? If set to false, all invoice items will use the same tax percent
taxPercent          | Number | No | Tax percent which will be used if multipleTaxesOnRows is set to false. This must be 0, 6, 12 or 25% and if not specified will be set to 25%.
currencyCode        | String | No | Currency code to be used on the invoice
currencyRate        | Number | No | Currency rate between SEK and the selected currency
notes               | String | No | Notes on the invoice
invoiceItems        | Array  | No | Array containing objects with invoice items. See below for details.
tags                | Array  | No | Array of tag ids
useFooterFromSettings| Boolean | No | Do you want to use the footer that's specified in the settings?
footerText          | String | No | Footer text which will be used if useFooterFromSettings is set to false


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

## Update an Invoice

```shell
curl -X PUT "https://app.seventime.se/api/2/invoices/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fb64449b0cc951024822167","customer":"571f21058d7f616498213765","modifiedByUser":"51718241fdb7894158127","language":"EN"}' 
```

```javascript
let jsonData = {
  _id: '5fb64449b0cc951024822167',
  modifiedByUser: '51718241fdb7894158127',
  invoiceName: 'Invoice 2020-12',
  customer: '571f21058d7f616498213765',
  multipleTaxesOnRows: 'true',
  taxPercent: 25,
  invoiceItems: [{...}, ...]
};

let options = {
  url: 'https://app.seventime.se/api/2/invoices',
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
    console.log("Invoice updated: " + body.invoiceName + ", _id: " + body._id);
  } else {
    console.error("ERROR! Unable to update invoice: " + error);
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
  "_id": "5fb64449b0cc951024822167",
  "createDate": "2020-11-19T10:09:13.039Z",
  "invoiceItems": [{...}, ...],
  "documents": [],
  "invoiceLogEntries":
   [ 
    { "_id": "5fb64449b0cc9510a561dfe0",
       "logType": 1,
       "description": "",
       "user": "5f48eb3e65d7e976825602",
       "userName": "Anna Andersson",
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
  "invoiceName": "Invoice 2020-12",
  "marking": "",
  "yourOrderNumber": "",
  "notes": "",
  "taxPercent": 25,
  "invoiceStatus": 2,
  "invoiceDate": "2020-11-19T10:09:13.033Z",
  "createdByUser": "5f48eb3e65d7ee494b523978"
  "createdByUserName": "Anna Andersson",
  "customer": "571f21058d7f618a264217895",
  "customerName": "Company AB",
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

This endpoint updates an invoice

### HTTP Request

`PUT https://app.seventime.se/api/2/invoices/`

### PUT Parameters

The table below shows the required fields or fields that differ from 'Create an Invoice'. Other available fields can be found in the section 'Create an Invoice'.

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                     | String | Yes | Id of the invoice
modifiedByUser          | String | Yes | Id of the user who modified the invoice
multipleTaxesOnRows     | Boolean| Yes | Should it be possible to use different tax rates on invoice rows?
taxPercent              | Boolean| Yes*| Tax rate on invoice rows *Required if 'multipleTaxesOnRows' is false.
invoiceItems            | Array  | Yes | Array containing the invoice items. See the section 'Create an Invoice' for more information about these items
invoiceStatus           | Number | No  | Invoice status. 1 for 'Draft', 2 for 'Sent', 3 for 'Paid' and 4 for 'Obliterated'. Note that changing the status to 'Sent' will not send the invoice, this will mark the invoice as sent and give the invoice a number. It is only possible to set the status to 'Paid' or 'Obliterated' on a sent invoice.

<!---
## Delete an Invoice

```shell
curl -X DELETE "https://app.seventime.se/api/2/invoices/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fb64449b0cc951024822167","deletedByUser":"5f48eb3e65d7ee494b523978"}' 
```

```javascript
let jsonData = {
  _id: '5fb64449b0cc951024822167',
  deletedByUser: '5f48eb3e65d7ee494b523978'
};

let options = {
  url: 'https://app.seventime.se/api/2/invoices',
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
    console.log("Invoice deleted: #" + body.invoiceNumber + ' ' + body.invoiceName);
  } else {
    console.error("ERROR! Unable to delete invoice: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "_id": "5fb64449b0cc951024822167",
  "invoiceName": "Invoice",
  "invoiceNumber": "24511",
}
"Invoice deleted: #24511 Invoice"
```

This endpoint deletes an invoice

### HTTP Request

`DELETE https://app.seventime.se/api/2/invoices/`

### DELETE Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id       | String | Yes | Id of the invoice
deletedByUser       | String | Yes | Id of the user who deleted the invoice
-->
