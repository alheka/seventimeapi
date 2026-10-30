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
      "createDate": "2019-01-07T17:15:08.532Z"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves quotes.

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
    "createDate": "2019-01-07T17:15:08.532Z"
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
