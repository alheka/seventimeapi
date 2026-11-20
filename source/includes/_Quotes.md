# Quotes
## Get Quotes

```shell
curl "https://app.seventime.se/api/2/quotes/?limit=5&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/quotes/?limit=5&page=1";
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
    "totalResources": 195,
    "totalPages": 98,
    "currentPage": 5
  },
  "data": [
    {
      "_id": "5c338913a1b2c3d4e5001164",
      "quoteNumber": "1054",
      "quoteType": 0,
      "quoteName": "Prisindikation",
      "quoteInfoName": "",
      "quoteCategory": null,
      "quoteCategoryName": null,
      "language": "SV",
      "description": null,
      "headerText": null,
      "footerInfoText": null,
      "footerText": "<table width=\"100%\"><tr><td style='vertical-align: top;'>TESTerrt</td><td style='vertical-align: top;'>TEST2</td><td style='vertical-align: top;'>TEST3</td></tr></table>",
      "createdByUser": "5f48eb3ea1b2c3d4e5001165",
      "createdByUserName": "Anna Andersson",
      "ourReference": "5f48eb3ea1b2c3d4e5001165",
      "ourReferenceName": "Anna Andersson",
      "salesAgent": "5f48eb3ea1b2c3d4e5001165",
      "salesAgentName": "Anna Andersson",
      "customer": "5bb26376a1b2c3d4e5001166",
      "customerName": "Company",
      "customerNumber": "44312",
      "customerAddress": "Östra Gatan 129 123 45 Stockholm",
      "customerVAT": "",
      "contactPerson": null,
      "contactPersonName": null,
      "project": null,
      "projectName": null,
      "workOrder": null,
      "workOrderName": "",
      "workOrderNumber": "",
      "quoteDate": "2019-01-07T17:13:55.271Z",
      "validToDate": "2019-02-06T17:13:55.383Z",
      "discountInPercent": 0,
      "totalAmount": 500,
      "totalTaxAmount": 125,
      "totalAmountInclTax": 625,
      "taxPercent": 25,
      "totalCost": 0,
      "useQuoteValue": false,
      "quoteValue": 0,
      "useQuoteCost": false,
      "quoteCost": 0,
      "currencyCode": "SEK",
      "currencyRate": 1,
      "quoteStatus": 3,
      "archived": false,
      "archivedDate": null,
      "deliveryDate": null,
      "deliveryDateEnd": null,
      "sentDate": "2019-01-07T17:15:10.109Z",
      "acceptedDate": "2019-01-07T00:00:00.000Z",
      "rejectedDate": null,
      "invoice": null,
      "invoiceNumber": "",
      "invoicedDate": null,
      "priceList": null,
      "priceListName": "",
      "marking": "",
      "houseDeductionBasisAmount": 0,
      "houseDeductionAmount": 0,
      "enableQuoteConditions": false,
      "quoteConditionsContent": "",
      "multipleTaxesOnRows": false,
      "showPriceInclTaxesOnRows": true,
      "confirmationDate": null,
      "confirmationHeaderText": "Härmed bekräftar vi er beställning enligt specifikationen nedan.",
      "confirmationFooterInfoText": "",
      "confirmationTitle": "Orderbekräftelse",
      "publicLink": "ObLBZZ0wDWcjlzxUwLnD",
      "useBudgetCalculation": false,
      "quoteAcceptReason": null,
      "quoteAcceptReasonName": null,
      "quoteDeclineReason": null,
      "quoteDeclineReasonName": null,
      "notes": "",
      "openNotificationSent": false,
      "quoteTemplate": "5b7dd2baa1b2c3d4e5001167",
      "stockReservationIsDone": false,
      "quoteElements": [
        {
          "_id": "5b7ada85a1b2c3d4e5001168",
          "content": {
            "text": "",
            "confirmationText": ""
          },
          "backgroundColor": "FAFAFA",
          "bottomMargin": 20,
          "topMargin": 20,
          "elementTypeId": 1000,
          "itemId": "0.1735729354019433"
        },
        {
          "_id": "5c25fd4e818921172d237086",
          "content": {
            "invoiceItems": [
              {
                "stockLocation": "5bbd3a49a1b2c3d4e5001169",
                "selectedFlag": false,
                "houseWorkTypeOfWork": 0,
                "houseWorkFlag": false,
                "totalCost": 0,
                "totalAmountInclTax": 0,
                "totalTaxAmount": 0,
                "totalAmount": 500,
                "taxPercent": 25,
                "discountPercent": 0,
                "supplementChargePercent": 0,
                "discountInPercent": 0,
                "unitCost": 0,
                "unit": "Styck",
                "priceListName": null,
                "priceList": null,
                "unitPrice": 100,
                "numberOfItems": "5",
                "machineName": "",
                "machine": null,
                "driverJournalItemTypeName": "",
                "driverJournalItemType": null,
                "expenseItemName": "Company - 5 användare - #2",
                "expenseItem": "5de78aed1332719657d4218b",
                "categoryName": "",
                "timeCategory": null,
                "itemType": "expense",
                "createDate": null,
                "articleNumber": "203",
                "itemOrder": 1024,
                "itemId": "0.29956387071628154",
                "description": "",
                "name": "",
                "_id": null
              }
            ],
            "totalAmount": 500,
            "totalTaxAmount": 125,
            "totalAmountInclTax": 625,
            "taxPercent": 25,
            "totalCost": 0,
            "houseDeductionBasisAmount": 0,
            "houseDeductionAmount": 0,
            "selectableRows": false,
            "showOnlyTotalPrice": false,
            "hiddenColumns": [
              "articleNumber"
            ]
          },
          "backgroundColor": "FAFAFA",
          "bottomMargin": 20,
          "topMargin": 20,
          "elementTypeId": 1200,
          "itemId": "0.086780107201752"
        },
        {
          "_id": "5b7a808ba1b2c3d4e5001170",
          "content": {
            "text": "",
            "confirmationText": ""
          },
          "backgroundColor": "FAFAFA",
          "bottomMargin": 20,
          "topMargin": 20,
          "elementTypeId": 1000,
          "itemId": "0.047508293157285886"
        }
      ],
      "budgetCalculation": {
        "invoiceItems": [],
        "totalBenefitAmount": 0,
        "totalCostAmount": 0
      },
      "houseProperties": {
        "typeOfProperty": 1,
        "propertyDescription": "",
        "housingSocietyNumber": "",
        "apartmentNumber": "",
        "maxDeductionAmount": 50000,
        "personalNumber": "",
        "deductionDistribution": []
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
      "quoteLogEntries": [
        {
          "_id": "5c33831ca1b2c3d4e5001171",
          "logDate": "2019-01-07T17:15:08.533Z",
          "userName": "Anna Andersson",
          "user": "59312765a1b2c3d4e5001172",
          "description": "",
          "logType": 1,
          "entryId": "mZjaXWo2oRTr"
        },
        {
          // ...
        }
      ],
      "invoiceItems": [],
      "createDate": "2019-01-07T17:15:08.532Z",
      "updatedAt": "2019-01-09T08:21:44.120Z"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves quotes.

<aside class="notice">
To keep the responses small, use <code>include</code> to only get the quote head and the parts you need, and <code>lastModified</code> to only get the quotes that have changed since your last call. The full quote is always available with <a href="#get-a-specific-quote">Get a specific Quote</a>.
</aside>

### HTTP Request

`GET https://app.seventime.se/api/2/quotes`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
quoteName                           |  | If specified, quotes that match the parameter will be included.
quoteNumber                         |  | If specified, quotes that match the parameter will be included.
fromQuoteDate                       |  | If specified, quotes with quote date after or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
toQuoteDate                         |  | If specified, quotes with quote date before or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
fromValidToDate                     |  | If specified, quotes with valid to date after or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
toValidToDate                       |  | If specified, quotes with valid to date before or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
lastModified                        |  | If specified, quotes that have been modified since the specified timestamp will be included (compared with `updatedAt`). Accepted formats: 'YYYY-MM-DD', 'YYYY-MM-DD HH:MM', 'YYYY-MM-DD HH:MM:SS', 'YYYY-MM-DDTHH:MM', 'YYYY-MM-DDTHH:MM:SS'
cursor       |  | `first` to page with a cursor instead of `page`, then `meta.nextCursor` from the previous response. Can't be combined with `page`, `sortBy` or `sortDirection`. See [Paging with a cursor](#paging-with-a-cursor)
include                             |  | If specified, only the quote head is returned plus the parts listed, comma separated: `invoiceItems`, `quoteElements`, `quoteConditionsContent`, `quoteLogEntries`, `budgetCalculation`, `documents`. Use `include=none` for the quote head only. If not specified, the full quotes are returned. Example: `include=invoiceItems,quoteLogEntries`
limit                               | 100 | Number of quotes per page. Maximum 500
page                                | 1 | Page number
sortBy                              |  | If specified, a sort will be made on the specified parameter
sortDirection                       |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get a specific Quote

```shell
curl "https://app.seventime.se/api/2/quotes/5c338913a1b2c3d4e5001164" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/quotes/5c338913a1b2c3d4e5001164";
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
    "_id": "5c338913a1b2c3d4e5001164",
    "quoteNumber": "1054",
    "quoteType": 0,
    "quoteName": "Prisindikation",
    "quoteInfoName": "",
    "quoteCategory": null,
    "quoteCategoryName": null,
    "language": "SV",
    "description": null,
    "headerText": null,
    "footerInfoText": null,
    "footerText": "<table width=\"100%\"><tr><td style='vertical-align: top;'>TESTerrt</td><td style='vertical-align: top;'>TEST2</td><td style='vertical-align: top;'>TEST3</td></tr></table>",
    "createdByUser": "5f48eb3ea1b2c3d4e5001173",
    "createdByUserName": "Anna Andersson",
    "ourReference": "5f48eb3ea1b2c3d4e5001173",
    "ourReferenceName": "Anna Andersson",
    "salesAgent": "5f48eb3ea1b2c3d4e5001173",
    "salesAgentName": "Anna Andersson",
    "customer": "5bb26376a1b2c3d4e5001174",
    "customerName": "Company",
    "customerNumber": "44312",
    "customerAddress": "Östra Gatan 129 123 45 Stockholm",
    "customerVAT": "",
    "contactPerson": null,
    "contactPersonName": null,
    "project": null,
    "projectName": null,
    "workOrder": null,
    "workOrderName": "",
    "workOrderNumber": "",
    "quoteDate": "2019-01-07T17:13:55.271Z",
    "validToDate": "2019-02-06T17:13:55.383Z",
    "discountInPercent": 0,
    "totalAmount": 500,
    "totalTaxAmount": 125,
    "totalAmountInclTax": 625,
    "taxPercent": 25,
    "totalCost": 0,
    "useQuoteValue": false,
    "quoteValue": 0,
    "useQuoteCost": false,
    "quoteCost": 0,
    "currencyCode": "SEK",
    "currencyRate": 1,
    "quoteStatus": 3,
    "archived": false,
    "archivedDate": null,
    "deliveryDate": null,
    "deliveryDateEnd": null,
    "sentDate": "2019-01-07T17:15:10.109Z",
    "acceptedDate": "2019-01-07T00:00:00.000Z",
    "rejectedDate": null,
    "invoice": null,
    "invoiceNumber": "",
    "invoicedDate": null,
    "priceList": null,
    "priceListName": "",
    "marking": "",
    "houseDeductionBasisAmount": 0,
    "houseDeductionAmount": 0,
    "enableQuoteConditions": false,
    "quoteConditionsContent": "",
    "multipleTaxesOnRows": false,
    "showPriceInclTaxesOnRows": true,
    "confirmationDate": null,
    "confirmationHeaderText": "Härmed bekräftar vi er beställning enligt specifikationen nedan.",
    "confirmationFooterInfoText": "",
    "confirmationTitle": "Orderbekräftelse",
    "publicLink": "ObLBZZ0wDWcjlxzUbYtLL",
    "useBudgetCalculation": false,
    "quoteAcceptReason": null,
    "quoteAcceptReasonName": null,
    "quoteDeclineReason": null,
    "quoteDeclineReasonName": null,
    "notes": "",
    "openNotificationSent": false,
    "quoteTemplate": "5b7dd2baa1b2c3d4e5001175",
    "stockReservationIsDone": false,
    "quoteElements": [
      {
        "_id": "5b7ada8ba1b2c3d4e5001176",
        "content": {
          "text": "",
          "confirmationText": ""
        },
        "backgroundColor": "FAFAFA",
        "bottomMargin": 20,
        "topMargin": 20,
        "elementTypeId": 1000,
        "itemId": "0.1735729354019433"
      },
      {
        "_id": "5c25fd4e8189211798574952",
        "content": {
          "invoiceItems": [
            {
              "stockLocation": "5bbd3a49dda7dbc364978521",
              "selectedFlag": false,
              "houseWorkTypeOfWork": 0,
              "houseWorkFlag": false,
              "totalCost": 0,
              "totalAmountInclTax": 0,
              "totalTaxAmount": 0,
              "totalAmount": 500,
              "taxPercent": 25,
              "discountPercent": 0,
              "supplementChargePercent": 0,
              "discountInPercent": 0,
              "unitCost": 0,
              "unit": "Styck",
              "priceListName": null,
              "priceList": null,
              "unitPrice": 100,
              "numberOfItems": "5",
              "machineName": "",
              "machine": null,
              "driverJournalItemTypeName": "",
              "driverJournalItemType": null,
              "expenseItemName": "Company - 5 användare - #2",
              "expenseItem": "5de78aeda1b2c3d4e5001177",
              "categoryName": "",
              "timeCategory": null,
              "itemType": "expense",
              "createDate": null,
              "articleNumber": "203",
              "itemOrder": 1024,
              "itemId": "0.29956387071628154",
              "description": "",
              "name": "",
              "_id": null
            }
          ],
          "totalAmount": 500,
          "totalTaxAmount": 125,
          "totalAmountInclTax": 625,
          "taxPercent": 25,
          "totalCost": 0,
          "houseDeductionBasisAmount": 0,
          "houseDeductionAmount": 0,
          "selectableRows": false,
          "showOnlyTotalPrice": false,
          "hiddenColumns": [
            "articleNumber"
          ]
        },
        "backgroundColor": "FAFAFA",
        "bottomMargin": 20,
        "topMargin": 20,
        "elementTypeId": 1200,
        "itemId": "0.086780107201752"
      },
      {
        "_id": "5b7a808ba1b2c3d4e5001178",
        "content": {
          "text": "",
          "confirmationText": ""
        },
        "backgroundColor": "FAFAFA",
        "bottomMargin": 20,
        "topMargin": 20,
        "elementTypeId": 1000,
        "itemId": "0.047508293157285886"
      }
    ],
    "budgetCalculation": {
      "invoiceItems": [],
      "totalBenefitAmount": 0,
      "totalCostAmount": 0
    },
    "houseProperties": {
      "typeOfProperty": 1,
      "propertyDescription": "",
      "housingSocietyNumber": "",
      "apartmentNumber": "",
      "maxDeductionAmount": 50000,
      "personalNumber": "",
      "deductionDistribution": []
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
    "quoteLogEntries": [
      {
        "_id": "5c33831ca1b2c3d4e5001179",
        "logDate": "2019-01-07T17:15:08.533Z",
        "userName": "Anna Andersson",
        "user": "59312765a1b2c3d4e5001180",
        "description": "",
        "logType": 1,
        "entryId": "mZjaXWo2oRTr"
      },
      {
        // ...
      }
    ],
    "invoiceItems": [],
    "createDate": "2019-01-07T17:15:08.532Z",
    "updatedAt": "2019-01-09T08:21:44.120Z"
  }
}
```

This endpoint retrieves a specific quote.


### HTTP Request

`GET https://app.seventime.se/api/2/quotes/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the quote to retrieve

## Get Quote Templates

```shell
curl "https://app.seventime.se/api/2/quoteTemplates" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/quoteTemplates/?";
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
    "totalResources": 8,
    "totalPages": 1,
    "currentPage": 1
  },
  "data": [
    {
      "_id": "5fb02816a1b2c3d4e5001181",
      "columnContents": [
        "This is a new footer!<br><br>"
      ],
      "templateName": "Standard utan sektioner",
      "quoteType": 0,
      "language": "",
      "createdByUser": "5f48eb3ea1b2c3d4e5001182",
      "createdByUserName": "Anna Andersson",
      "createDate": "2020-11-09T13:31:10.929Z",
      "documents": [],
      "quoteElements": [
        {
          "_id": "5b7a808ba1b2c3d4e5001183",
          "itemId": "0.2991772478801382",
          "elementTypeId": 1400,
          "topMargin": 20,
          "bottomMargin": 20,
          "backgroundColor": "FAFAFA",
          "content": null
        }
      ],
      "overrideFooter": false,
      "footerText": "<table width=\"100%\"><tr><td style='vertical-align: top;'>This is a new footer!<br><br></td></tr></table>",
      "footerNumOfCols": 1,
      "overrideLogoAndAddress": false,
      "logo": [
        {
          "_id": "5f6b5b15a1b2c3d4e5001184",
          "createDate": "2020-09-23T14:26:29.655Z",
          "modifiedDate": "2020-09-23T14:26:29.655Z",
          "name": "logo.png",
          "contentType": "image/png",
          "size": 6765,
          "user": "5f48eb3ea1b2c3d4e5001185",
          "userName": "Anna Andersson"
        }
      ],
      "logotypeWidth": 200,
      "logoPosition": "left",
      "quoteAddress": "<b>Företaget</b><div>Gatan</div><div>12345 Staden</div>"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves quote templates.

### HTTP Request

`GET https://app.seventime.se/api/2/quoteTemplates`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
templateName                        |  | If specified, quote templates that match the parameter will be included.
sortBy                              |  | If specified, a sort will be made on the specified parameter
sortDirection                       |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get Quote Categories

```shell
curl "https://app.seventime.se/api/2/quoteCategories" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/quoteCategories/?";
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
    "totalResources": 8,
    "totalPages": 1,
    "currentPage": 1
  },
  "data": [
    {
      "_id": "58a678badc33073a42215684",
      "isActive": true,
      "quoteCategoryName": "Utbildning"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves quote categories.

### HTTP Request

`GET https://app.seventime.se/api/2/quoteCategories`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
quoteCategoryName                   |  | If specified, quote categories that match the parameter will be included.
sortBy                              |  | If specified, a sort will be made on the specified parameter
sortDirection                       |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Create a Quote

```shell
curl -X POST "https://app.seventime.se/api/2/quotes" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"quoteTemplate":"5fb02816a1b2c3d4e5001181","customer":"571f2105a1b2c3d4e5001108","createdByUser":"51718241fdb7084835249227","invoiceItems":[{"itemType":"expense","articleNumber":"203","numberOfItems":5},{"itemType":"timelog","timeCategory":"5f48eb3ea1b2c3d4e5001190","numberOfItems":8}]}'
```

```javascript
let jsonData = {
  quoteTemplate: '5fb02816a1b2c3d4e5001181',
  customer: '571f2105a1b2c3d4e5001108',
  createdByUser: '51718241fdb7084835249227',
  invoiceItems: [
    { itemType: 'expense', articleNumber: '203', numberOfItems: 5 },
    { itemType: 'timelog', timeCategory: '5f48eb3ea1b2c3d4e5001190', numberOfItems: 8 }
  ]
};

let options = {
  url: 'https://app.seventime.se/api/2/quotes',
  json: jsonData,
  headers: {
    "Client-Secret": "thisismysecretkey",
    "Content-Type": "application/json",
    "Accept": 'application/json'
  }
};

request.post(options, function (error, response, body) {
  if (!error && response.statusCode === 200) {
    console.log("Quote created: _id: " + body._id);
  } else {
    console.error("ERROR! Unable to create quote: " + (body && body.errorMessage));
  }
});
```

> The above command returns JSON structured like this:

```json
{
  "_id": "6930a1f2a1b2c3d4e5001201",
  "quoteType": 0,
  "quoteStatus": 1,
  "quoteName": "Offert",
  "quoteInfoName": "",
  "quoteTemplate": "5fb02816a1b2c3d4e5001181",
  "quoteCategory": null,
  "quoteCategoryName": null,
  "language": "SV",
  "createdByUser": "51718241fdb7084835249227",
  "createdByUserName": "Anna Andersson",
  "ourReference": "51718241fdb7084835249227",
  "ourReferenceName": "Anna Andersson",
  "customer": "571f2105a1b2c3d4e5001108",
  "customerName": "Company",
  "customerNumber": "44312",
  "customerAddress": "Östra Gatan 129<br>123 45 Stockholm",
  "customerVAT": "",
  "quoteDate": "2026-11-19T23:00:00.000Z",
  "validToDate": "2026-12-19T23:00:00.000Z",
  "createDate": "2026-11-20T14:12:31.207Z",
  "totalAmount": 5700,
  "totalTaxAmount": 1425,
  "totalAmountInclTax": 7125,
  "taxPercent": 25,
  "totalCost": 3100,
  "currencyCode": "SEK",
  "currencyRate": 1,
  "marking": "",
  "yourOrderNumber": "",
  "notes": "",
  "enableQuoteConditions": true,
  "quoteConditionsContent": "<p>Villkor</p>",
  "multipleTaxesOnRows": false,
  "showPriceInclTaxesOnRows": false,
  "publicLink": "ObLBZZ0wDWcjlxzUbYtLL",
  "quoteElements": [
    {
      "itemId": "0.1735729354019433",
      "elementTypeId": 1000,
      "content": {
        "text": "Tack för er förfrågan!"
      }
    },
    {
      "itemId": "0.086780107201752",
      "elementTypeId": 1200,
      "content": {
        "invoiceItems": [
          {
            "itemId": "0.4196323818927584",
            "itemOrder": 1024,
            "itemType": "expense",
            "expenseItem": "5de78aeda1b2c3d4e5001177",
            "expenseItemName": "Kabel",
            "articleNumber": "203",
            "description": "",
            "numberOfItems": 5,
            "unit": "m",
            "unitPrice": 100,
            "unitCost": 60,
            "discountPercent": 0,
            "taxPercent": 25,
            "totalAmount": 500,
            "totalTaxAmount": 125,
            "totalAmountInclTax": 625,
            "totalCost": 300
          },
          {
            "itemId": "0.7710563215462096",
            "itemOrder": 2048,
            "itemType": "time",
            "timeCategory": "5f48eb3ea1b2c3d4e5001190",
            "categoryName": "Montör",
            "articleNumber": "",
            "description": "",
            "numberOfItems": 8,
            "unit": "tim",
            "unitPrice": 650,
            "unitCost": 350,
            "discountPercent": 0,
            "taxPercent": 25,
            "totalAmount": 5200,
            "totalTaxAmount": 1300,
            "totalAmountInclTax": 6500,
            "totalCost": 2800
          }
        ],
        "taxPercent": 25,
        "totalAmount": 5700,
        "totalTaxAmount": 1425,
        "totalAmountInclTax": 7125,
        "totalCost": 3100
      }
    },
    {
      // ...
    }
  ],
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
  "tags": [],
  "quoteLogEntries": [
    {
      "_id": "6930a1f2a1b2c3d4e5001202",
      "logType": 1,
      "description": "",
      "user": "51718241fdb7084835249227",
      "userName": "Anna Andersson",
      "logDate": "2026-11-20T14:12:31.207Z"
    }
  ]
  // ...
}
"Quote created: _id: 6930a1f2a1b2c3d4e5001201"
```

This endpoint creates a quote or an opportunity from a quote template, as when a quote is created from the template in Seven Time:

* The quote gets the template's sections, texts in the quote's language, documents, category and VAT settings, and the defaults of the quote settings (e.g. the number of days the quote is valid, the terms and the footer).
* The quote gets the customer's name, number, address, VAT number, delivery address and price lists.
* The rows in `invoiceItems` are added to the template's first price table, after any rows the template already has. A row gets the same name, unit, VAT rate, cost and price as when the article, time category or machine is chosen on a new row in Seven Time, from the customer's price lists, the project's prices, discounts and markups. Values specified on the row replace the calculated ones.
* If the article is a bundle, its articles are added as rows after it, as in Seven Time. They are hidden on the quote if the bundle is set to not show its articles.
* The totals of the price tables and the quote are calculated.

The webhook event `quote.created` is sent, and the seller (`salesAgent`) is notified as in Seven Time. The created quote is returned directly (not wrapped in a `data` property), with the same fields as [Get a specific Quote](#get-a-specific-quote).

Only drafts, opportunities and normal quotes can be created. ROT, RUT and green deduction quotes can't be created through the API yet.

Validation errors (e.g. a missing required field, an id that is not found or an invalid value) return HTTP 400 with a descriptive `errorMessage`, and nothing is created. HTTP 500 is only returned for server errors.

With an OAuth access token, the user needs the permission to work with quotes. Without the permission to see costs on quotes, `unitCost` is ignored and the costs are calculated by Seven Time.

### HTTP Request

`POST https://app.seventime.se/api/2/quotes`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
quoteTemplate       | String | Yes | Id of the quote template. See [Get Quote Templates](#get-quote-templates). The template must be active
customer            | String | Yes | Id of the customer
createdByUser       | String | Yes | Id of the user who created the quote. The user is also set as our reference if `ourReference` is not specified
quoteStatus         | Number | No | 1 for 'Draft' and 10 for 'Opportunity'. If not specified, this will be set to 1. A quote can't be created as sent
quoteType           | Number | No | Type of quote. Only 0 (Normal) can be created
language            | String | No | Language of the quote given as a language code, e.g. SV or EN. Must be one of the languages in the quote settings. If not specified, this will be set to the only language in the quote settings, else SV
quoteName           | String | No | Name of the quote. If not specified, this will be set to the quote name in the quote settings for the language, and for an opportunity to 'Opportunity' translated to the language
quoteDate           | String | No | Quote date. Has to be in the format YYYY-MM-DD. If not specified, this will be set to the current date
validToDate         | String | No* | Date the quote is valid to. Has to be in the format YYYY-MM-DD. If not specified, this will be set to the quote date + the number of days a quote is valid in the quote settings. *Required for a quote (not an opportunity) if the quote settings have no number of days
ourReference        | String | No | Id of the user that will be set as our reference
salesAgent          | String | No | Id of the user that will be set as the seller
contactPerson       | String | No | Id of the contact person. Must be a contact person of the customer. If `marking` is not specified, the contact person's marking is used
project             | String | No | Id of the project of the quote. If the project has a delivery address, it is used instead of the customer's
objectItem          | String | No | Id of the object item
quoteCategory       | String | No | Id of the quote category. See [Get Quote Categories](#get-quote-categories). If not specified, the template's category is used
marking             | String | No | Marking on the quote
yourOrderNumber     | String | No | Your order number
notes               | String | No | Notes on the quote
deliveryAddress     | Object | No | Delivery address. Replaces the delivery address of the customer and the project. Same attributes as `deliveryAddress` in [Create an Invoice](#create-an-invoice)
tags                | Array  | No | Array of quote tag ids
invoiceItems        | Array  | No | Array containing objects with the rows of the quote. See below for details. If the template has no price table, rows can't be specified

**Attributes for invoiceItems**

The field invoiceItems should be an array containing objects with the attributes shown below

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
itemType              | String | Yes | Item type of the row, see below for details
expenseItem           | String | No* | Id of the expense item. *For itemType expense, expenseItem or articleNumber is required
articleNumber         | String | No* | For itemType expense without expenseItem: the expense item is looked up by its article number, first among the account's active expense items and then among the expense items of the account's wholesalers. The article number must match exactly one expense item. For itemType general: the article number shown on the row
timeCategory          | String | No* | Id of the time category. *Required if itemType is timelog. Must be invoiceable and not an absence type
machine               | String | No* | Id of the machine. *Required if itemType is machineTimeLog
description           | String | No  | Description of the row, or the text of a text row. If not specified, the description of the expense item is used
name                  | String | No  | For itemType general: used as the description if `description` is not specified
numberOfItems         | Number | No  | Quantity of the item. If not specified, this will be set to 1
unit                  | String | No  | Unit of the item. If not specified, the unit of the expense item is used, 'tim' for time and machine rows and 'st' for general rows
unitPrice             | Number | No  | Unit price of the item. If not specified, the price is calculated as in Seven Time
pricePerHour          | Number | No  | Price per hour for timelog rows. Same as unitPrice
unitCost              | Number | No  | Purchase price of the item. If not specified, the cost is calculated as in Seven Time
discountPercent       | Number | No  | Discount of the item. Can only be specified if "Discount on rows" is enabled in the quote settings. If not specified, the customer's discount is used when the setting is enabled
taxPercent            | Number | No  | Tax percent of the item, between 0 and 100. Only used if the template has different taxes on the rows. If not specified, the tax percent of the expense item or the price table is used

**Item types**

Item type |  Description
--------- |-----------
expense        | Expense row
timelog        | Time log row
machineTimeLog | Machine time log row
general        | Free-text row
text           | Text row
blank          | Blank row
