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
    "totalResourcesIsExact": true,
    "totalPages": 663,
    "currentPage": 9,
    "hasMore": true,
    "nextPage": 10
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
            "_id": "5fae99b0a1b2c3d4e5001077",
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
        "5fa2b550a1b2c3d4e5001078",
        // ...
      ],
      "tags": [
        "5f742440d608b220152b1549",
        "5f74243ad608b22058126b12"
      ],
      "createDate": "2020-11-13T14:35:28.797Z",
      "invoiceItems": [
        {
          "_id": "5fae99b0a1b2c3d4e5001079",
          "createDate": "2020-11-13T14:35:28.795Z",
          "houseWorkTypeOfWork": 1,
          "name": "**Skivhantel i Gummi 10 Kg****",
          "description": "Skivhantel av järn",
          "expenseItem": "5de78ae9a1b2c3d4e5001080",
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
          "_id": "5fae99b0a1b2c3d4e5001081",
          "logDate": "2020-11-13T14:35:28.797Z",
          "logType": 1,
          "description": "",
          "user": "51714655a1b2c3d4e5001082",
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
      "createdByUser": "51714655a1b2c3d4e5001083",
      "createdByUserName": "Anna Andersson",
      "customer": "5cc05b6aa1b2c3d4e5001084",
      "customerName": "Company AB",
      "dueDate": "2020-12-04T23:00:00.000Z",
      "actualDeliveryDate": "2020-11-02T23:00:00.000Z",
      "language": "EN",
      "project": "5b20cce1a1b2c3d4e5001085",
      "projectName": "Blåsippan",
      "contactPerson": "5af95e6ba1b2c3d4e5001086",
      "contactPersonName": "Anna Andersson",
      "ourReference": "518ff209a1b2c3d4e5001087",
      "ourReferenceName": "Anna Andersson",
      "workOrder": "5fa2b550a1b2c3d4e5001088",
      "workOrderNumber": "4843",
      "invoiceType": 1,
      "resultUnit": "5784ff52a1b2c3d4e5001089",
      "resultUnitName": "Kontor Nord",
      "priceList": "57bc1871a1b2c3d4e5001090",
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
customerName        |  | If specified, invoices where the customer name exactly matches the parameter will be included.
fromInvoiceDate     |  | If specified, invoices with invoice date after or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
toInvoiceDate       |  | If specified, invoices with invoice date before or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
fromDueDate         |  | If specified, invoices with due date after or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
toDueDate           |  | If specified, invoices with due date before or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
sortBy              | invoiceDate | If specified, a sort will be made on the specified parameter
sortDirection       | ascending | "ascending" or "descending". Applies to sortBy, or to invoiceDate if sortBy is not specified
limit               | 100 | Number of results per page (1-500). See 'Pagination'
page                | 1 | Page to retrieve. See 'Pagination'

An invalid date in any of the date parameters returns HTTP 400 with the `errorMessage` "Invalid fromDate" or "Invalid toDate".


## Get a specific Invoice

```shell
curl "https://app.seventime.se/api/2/invoices/5fab29b0a1b2c3d4e5001091" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/invoices/5fab29b0a1b2c3d4e5001091";
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
          "_id": "5fae99b0a1b2c3d4e5001092",
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
      "5fa2b550a1b2c3d4e5001093"
    ],
    "externalSystemExport": [],
    "tags": [
      "5f742440a1b2c3d4e5001094",
      "5f74243aa1b2c3d4e5001095"
    ],
    "_id": "5fae99b0a1b2c3d4e5001096",
    "createDate": "2020-11-13T14:35:28.797Z",
    "invoiceItems": [
      {
        "createDate": "2020-11-13T14:35:28.795Z",
        "_id": "5fae99b0a1b2c3d4e5001097",
        "houseWorkTypeOfWork": 1,
        "name": "**Skivhantel i Gummi 10 Kg****",
        "description": "Skivhantel av järn",
        "expenseItem": "5de78ae9a1b2c3d4e5001098",
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
        "user": "51714655a1b2c3d4e5001099",
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
        "_id": "5fb5217ea1b2c3d4e5001100",
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
    "createdByUser": "51714655a1b2c3d4e5001101",
    "createdByUserName": "Anna Andersson",
    "customer": "5cc05b6aa1b2c3d4e5001102",
    "customerName": "Company AB",
    "dueDate": "2020-12-04T23:00:00.000Z",
    "actualDeliveryDate": "2020-11-02T23:00:00.000Z",
    "language": "EN",
    "project": "5b20cce1d59a979134679582",
    "projectName": "Blåsippan",
    "contactPerson": "5af95e6ba1b2c3d4e5001103",
    "contactPersonName": "Anna Andersson",
    "ourReference": "518ff209a1b2c3d4e5001104",
    "ourReferenceName": "Anna Andersson",
    "workOrder": "5fa2b550a1b2c3d4e5001105",
    "workOrderNumber": "4843",
    "invoiceType": 1,
    "resultUnit": "5784ff52a1b2c3d4e5001106",
    "resultUnitName": "Kontor Nord",
    "priceList": "57bc1871a1b2c3d4e5001107",
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

This endpoint retrieves invoice tags. The tags are sorted by tagName. If no invoice tags have been created for the account, an empty array (`[]`) is returned without the `data` wrapper.



### HTTP Request

`GET https://app.seventime.se/api/2/invoiceTags/`

### URL Parameters

No parameters

## Create an Invoice
```shell
curl -X POST "https://app.seventime.se/api/2/invoices/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"invoiceStatus":2,"customer":"571f2105a1b2c3d4e5001108","createdByUser":"51718241fdb7084835249227","language":"EN"}' 
```

```javascript
let jsonData = {
  invoiceStatus: 2,
  customer: '571f2105a1b2c3d4e5001108',
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
    { "_id": "5fb64449a1b2c3d4e5001109",
       "logType": 1,
       "description": "",
       "user": "5f48eb3ea1b2c3d4e5001110",
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
  "customer": "571f2105a1b2c3d4e5001108",
  "customerName": "Company",
  "dueDate": "2020-12-09T22:59:59.999Z",
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

This endpoint creates an invoice. The created invoice is returned directly (not wrapped in a `data` property).

Missing `customer`, `createdByUser` or `language` returns HTTP 400. Other validation errors (e.g. an id that is not found or an invalid value) are also returned with HTTP 400 and a descriptive `errorMessage`. HTTP 500 is only returned for server errors.

### HTTP Request

`POST https://app.seventime.se/api/2/invoices/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
customer            | String | Yes | Customer id for the customer who the invoice should belong to
createdByUser       | String | Yes | Id of the user who created the invoice
language            | String | Yes | Language of the invoice given as a language code. Must be SV (Swedish) or EN (English)
name                | String | No | Name of the invoice. If not specified, this will be set to 'Invoice' translated to the selected language
invoiceDate         | String | No | Invoice date. Has to be in the format YYYY-MM-DD. If not specified, this will be set to the current date
dueDate             | String | No | Due date. Has to be in the format YYYY-MM-DD. If not specified, this will be set to the invoice date + the customer's payment days, or + the default payment terms if the customer has no payment days
actualDeliveryDate  | String | No | Delivery date ("Leveransdatum"), i.e. the date when the goods were delivered or the service was performed. Has to be in the format YYYY-MM-DD. Shown on the invoice if "Show delivery date" is enabled in the invoice settings, and included when the invoice is exported to an economy system
project             | String | No | Id of the project of the invoice
marking             | String | No | Marking on the invoice
yourOrderNumber     | String | No | Your order number
invoiceStatus       | Number | No | Status of the invoice. 1 for 'Draft' and 2 for 'Sent'
contactPerson       | String | No | Id of the contact person
ourReference        | String | No | Id of the user that will be set as our reference.
deliveryAddress     | Object | No | Contains attributes for delivery address. See below for details
workOrder           | String | No | Id of the work order. The work order must belong to the specified customer, and to the specified project if project is specified. If actualDeliveryDate is not specified and "Get the delivery date from the work order's completion date" is enabled in the invoice settings, the delivery date is set to the date the work order was completed
resultUnit          | String | No | Id of the result unit
invoiceType         | Number | No | Type of invoice. 0 for Normal, 1 for ROT, 2 for RUT and 3 for construction
houseProperties     | Object | No* | *Required if invoiceType is set to 1 or 2. See below for details
priceList           | String | No | Id of the price list to be used. If specified, prices from the price list will be used for invoice items
multipleTaxesOnRows | Boolean | No | Should it be possible to set different taxes on invoice items? If set to false, all invoice items will use the same tax percent
taxPercent          | Number | No | Tax percent which will be used if multipleTaxesOnRows is set to false. Must be a number. If not specified, this will be set to 25.
currencyCode        | String | No | Currency code to be used on the invoice. Must be SEK or EUR
currencyRate        | Number | No | Currency rate between SEK and the selected currency. Only used if currencyCode is not SEK
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
expenseItem           | String | No* | Id of the expense item. *For itemType expense, one of expenseItem, articleNumber or name is required. If no expense item is found, the row is created as a free-text (general) row using articleNumber/name
articleNumber         | String | No  | Article number. Used for expense rows without an expenseItem
name                  | String | No  | Name of the row. Used for expense and timelog rows. If not specified, the name of the expense item/time category is used
description           | String | No  | Description of the row
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
taxPercent            | Number | No  | Tax percent of the item. Only used if multipleTaxesOnRows is true. If not specified, this will be set to 25.
houseWorkTypeOfWork   | Number | No  | Type of work for the row. Used if invoiceType is 1 or 2. See below for details

**Item types**

This table contains the different item types used in the field invoiceItems.itemTypes

Item type |  Description
--------- |-----------
expense        | Expense row
timelog        | Time log row
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
  -d '{"_id":"5fb64449b0cc951024822167","customer":"571f21058d7f616498213765","modifiedByUser":"51718241a1b2c3d4e5001111","language":"EN"}' 
```

```javascript
let jsonData = {
  _id: '5fb64449b0cc951024822167',
  modifiedByUser: '51718241a1b2c3d4e5001111',
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
    { "_id": "5fb64449a1b2c3d4e5000501",
       "logType": 1,
       "description": "",
       "user": "5f48eb3ea1b2c3d4e5001112",
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
  "createdByUser": "5f48eb3e65d7ee494b523978",
  "createdByUserName": "Anna Andersson",
  "customer": "571f2105a1b2c3d4e5001113",
  "customerName": "Company AB",
  "dueDate": "2020-12-09T22:59:59.999Z",
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

This endpoint updates an invoice. The updated invoice is returned directly (not wrapped in a `data` property). The fields createdByUser, createdByUserName and invoiceNumber are ignored. If invoiceItems is specified, it replaces all existing invoice items.

Missing `_id` or `modifiedByUser` returns HTTP 400. Other validation errors (e.g. an id that is not found or an invalid value) are also returned with HTTP 400 and a descriptive `errorMessage`. HTTP 500 is only returned for server errors.

If `__v` is specified and the invoice has been modified since it was fetched, the update is rejected with HTTP 409 and the `errorMessage` "Invoice has been modified by another user. Reload before saving." Fetch the invoice again and retry with the new `__v`.

### HTTP Request

`PUT https://app.seventime.se/api/2/invoices/`

### PUT Parameters

The table below shows the required fields or fields that differ from 'Create an Invoice'. Other available fields can be found in the section 'Create an Invoice'.

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                     | String | Yes | Id of the invoice
modifiedByUser          | String | Yes | Id of the user who modified the invoice
__v                     | Number | No  | Version of the invoice, as returned when the invoice was fetched. Increased by every update. If specified, the update is only made if the invoice has not been modified since (otherwise HTTP 409). If not specified, the invoice is updated regardless of other changes
multipleTaxesOnRows     | Boolean| No  | Should it be possible to use different tax rates on invoice rows?
taxPercent              | Number | No* | Tax rate on invoice rows *Required if 'multipleTaxesOnRows' is false.
invoiceItems            | Array  | No  | Array containing the invoice items. Replaces the existing invoice items. See the section 'Create an Invoice' for more information about these items
actualDeliveryDate      | String | No  | Delivery date in the format YYYY-MM-DD. Send null or an empty string to remove the delivery date. If the field is not sent, the existing delivery date is kept
invoiceStatus           | Number | No  | Invoice status. 1 for 'Draft', 2 for 'Sent', 3 for 'Paid' and 4 for 'Obliterated'. Note that changing the status to 'Sent' will not send the invoice, this will mark the invoice as sent and give the invoice a number. It is only possible to set the status to 'Paid' or 'Obliterated' on a sent invoice.

<aside class="notice">
DELETE Invoices is not documented because this route is not currently implemented.
</aside>

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
