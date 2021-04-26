# Expenses

## Get Expenses

```shell
curl "https://app.seventime.se/api/2/expenses/?limit=2&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/expenses/?limit=2&page=1";
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
    "totalResources": 622,
    "totalPages": 311,
    "currentPage": 3
  },
  "data": [
    {
      "_id": "53ad291839f16d23a6414604d2",
      "attestedBy": null,
      "createDate": "2014-06-27T08:11:15.954Z",
      "customer": null,
      "customerName": "",
      "description": "",
      "documents": [],
      "expenseItem": "52d92f32d5fcf8941893174ab",
      "isAttested": false,
      "isInvoiceable": true,
      "isInvoiced": false,
      "name": "Arbetsordermodul2",
      "numberOfItems": 1,
      "project": "516fad2b265135db78024621§",
      "projectName": "Glimminge",
      "supplementOrder": false,
      "timestamp": "2014-06-27T00:00:00.000Z",
      "totalAmount": 20,
      "totalAmountAfterDiscount": 20,
      "totalAmountInclTax": 25,
      "totalTaxAmount": 5,
      "unit": "st",
      "unitCost": 20,
      "unitPrice": 20,
      "unitPriceInclTax": 25,
      "unitTax": 5,
      "user": "51203146506d961c030791801",
      "userName": "Tommy Hellström",
      "workOrder": null,
      "workOrderNumber": 0,
      "workOrderTitle": "",
      "unitPriceAfterDiscount": 20,
      "discountPercent": 0,
      "unitTaxPercent": 25,
      "doReimburse": false,
      "salaryCompilation": null,
      "verificationNumber": "",
      "distributor": null,
      "distributorName": "",
      "totalCost": 20,
      "articleNumber": "208"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves expenses.

### HTTP Request

`GET https://app.seventime.se/api/2/expenses`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
name               |  | If specified, expenses that match the parameter will be included.
articleNumber      |  | If specified, expenses that match the parameter will be included.
customer           |  | If specified, expenses that match the parameter will be included.
project            |  | If specified, expenses that match the parameter will be included.
distributor        |  | If specified, expenses that match the parameter will be included.
fromDate           |  | If specified, expenses registered after or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
toDate             |  | If specified, expenses registered before or on this date will be included. The date has to be in the format 'YYYY-MM-DD'
sortBy             |  | If specified, a sort will be made on the specified parameter
sortDirection      |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending




## Get a specific Expense

```shell
curl "https://app.seventime.se/api/2/expenses/53ad291839f16d23a6414604d2" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/expenses/53ad291839f16d23a6414604d2";
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
    "_id": "53ad291839f16d23a6414604d2",
    "attestedBy": null,
    "createDate": "2014-06-27T08:11:15.954Z",
    "customer": null,
    "customerName": "",
    "description": "",
    "documents": [],
    "expenseItem": "52d92f32d5fcf8941893174ab",
    "isAttested": false,
    "isInvoiceable": true,
    "isInvoiced": false,
    "name": "Arbetsordermodul2",
    "numberOfItems": 1,
    "project": "516fad2b265135db78024621§",
    "projectName": "Glimminge",
    "supplementOrder": false,
    "timestamp": "2014-06-27T00:00:00.000Z",
    "totalAmount": 20,
    "totalAmountAfterDiscount": 20,
    "totalAmountInclTax": 25,
    "totalTaxAmount": 5,
    "unit": "st",
    "unitCost": 20,
    "unitPrice": 20,
    "unitPriceInclTax": 25,
    "unitTax": 5,
    "user": "51203146506d961c030791801",
    "userName": "Tommy Hellström",
    "workOrder": null,
    "workOrderNumber": 0,
    "workOrderTitle": "",
    "unitPriceAfterDiscount": 20,
    "discountPercent": 0,
    "unitTaxPercent": 25,
    "doReimburse": false,
    "salaryCompilation": null,
    "verificationNumber": "",
    "distributor": null,
    "distributorName": "",
    "totalCost": 20,
    "articleNumber": "208"
  }
}
```

This endpoint retrieves a specific expense.



### HTTP Request

`GET https://app.seventime.se/api/2/expenses/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the expense to retrieve

## Get Expenses Items

```shell
curl "https://app.seventime.se/api/2/expenseItems/?limit=10&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/expenseItems/?limit=10&page=1";
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
    "totalResources": 19478,
    "totalPages": 1948,
    "currentPage": 176
  },
  "data": [
    {
      "_id": "5de78aed1332719192362bed",
      "description": "",
      "tax": 25,
      "articleNumber": "601310",
      "name": "10-pack Reaktionsbollar",
      "unitPrice": 295.59,
      "unitCost": 221,
      "unit": "St",
      "isInvoiceable": true,
      "isCategory": false,
      "parentExpenseItem": null,
      "parentExpenseItemName": "",
      "createDate": "2019-12-04T10:31:06.603Z",
      "bundledArticles": [],
      "alwaysReimburse": false,
      "isActive": true,
      "categoryGroupNumber": "",
      "articleGroupNumber": "",
      "distributor": null,
      "distributorName": "",
      "isInventoryItem": false,
      "unitPriceInclTax": 369.48749999999995
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves expense items.

### HTTP Request

`GET https://app.seventime.se/api/2/expenses`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
name                    |  | If specified, expense items that match the parameter will be included.
articleNumber           |  | If specified, expense items that match the parameter will be included.
distributorName         |  | If specified, expense items that match the parameter will be included.
description             |  | If specified, expense items that match the parameter will be included.
parentExpenseItemName   |  | If specified, expense items that match the parameter will be included.
isInvoiceable           |  | If specified, expense items that match the parameter will be included.
isActive                |  | If specified, expense items that match the parameter will be included.
favorite                |  | If specified, expense items that match the parameter will be included.
sortBy                  |  | If specified, a sort will be made on the specified parameter
sortDirection           |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending




## Get a specific Expense Item

```shell
curl "https://app.seventime.se/api/2/expenseItems/5de78aed1332719192362bed" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/expenseItems/5de78aed1332719192362bed";
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
    "_id": "5de78aed1332719192362bed",
    "description": "",
    "tax": 25,
    "articleNumber": "601310",
    "name": "10-pack Reaktionsbollar",
    "unitPrice": 295.59,
    "unitCost": 221,
    "unit": "St",
    "isInvoiceable": true,
    "isCategory": false,
    "parentExpenseItem": null,
    "parentExpenseItemName": "",
    "createDate": "2019-12-04T10:31:06.603Z",
    "bundledArticles": [],
    "alwaysReimburse": false,
    "isActive": true,
    "categoryGroupNumber": "",
    "articleGroupNumber": "",
    "distributor": null,
    "distributorName": "",
    "isInventoryItem": false,
    "unitPriceInclTax": 369.48749999999995
  }
}
```

This endpoint retrieves a specific expense item.



### HTTP Request

`GET https://app.seventime.se/api/2/expenseItems/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the expense item to retrieve


## Create an Expense

```shell
  curl -X POST "https://app.seventime.se/api/2/expenses/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"createdByUser":"5f48eb3e65d7ee4942c46eeb","user":"51203146506d961c030791801","expenseItem":"5de78aed1332719192362bed"}'
```

```javascript
let jsonData = {
  createdByUser: '5f48eb3e65d7ee4942c46eeb',
  user: '51203146506d961c030791801',
  expenseItem: '5de78aed1332719192362bed'
};

let options = {
  url: 'https://app.seventime.se/api/2/expenses',
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
    console.log("Expense created: _id: " + body._id);
  } else {
    console.error("ERROR! Unable to create expense: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "isInvoiceable": true,
  "_id": "5fbe684416625651d7f43257",
  "timestamp": "2020-11-25T14:20:52.129Z",
  "documents": [],
  "createDate": "2020-11-25T14:20:52.129Z",
  "bundledArticles": [],
  "customFields": [],
  "systemAccount": "5112826056d961c030000001",
  "numberOfItems": 1,
  "user": "51203146506d961c030791801",
  "userName": "Tommy Hellström",
  "expenseItem": "5de78aed1332719192362bed",
  "articleNumber": "575733",
  "name": "10-pack Reaktionsbollar",
  "description": "Skivhantel av järn",
  "distributor": "573c52cdf609f5692351914b",
  "distributorName": "Lev 4",
  "unit": "St",
  "unitCost": 319,
  "unitTaxPercent": 25,
  "unitPrice": 426.66,
  "unitPriceAfterDiscount": 426.66,
  "discountPercent": 0,
  "unitTax": 106.665,
  "unitPriceInclTax": 533.325,
  "totalTaxAmount": 106.665,
  "totalAmount": 426.66,
  "totalAmountAfterDiscount": 426.66,
  "totalCost": 319,
}
"Expense created: _id: 5fbe684416625651d7f43257"
```

This endpoint creates an expense

### HTTP Request

`POST https://app.seventime.se/api/2/expenses/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
createdByUser       | String | Yes | Id of the user who created the expense
user                | String | Yes | Id of the user on the expense
expenseItem         | String | Yes*| Id of the expense item. *Required if freetext for articles is not activated
name                | String | Yes*| Name of the article. *Required if expenseItem is not specified. This will set the article to freetext and is only possible if the setting for this is enabled.
workOrder           | String | No  | Id of the work order
customer            | String | No  | Id of the customer. If workOrder is specified, the customer from the work order will be used
project             | String | No  | Id of the project. If workOrder is specified, the project from the work order will be used
distributor         | String | No  | Id of the distributor
numberOfItems       | String | No  | Number of items
unit                | String | No  | Unit of the number of items
unitCost            | Number | No* | Cost per unit. If not specified, the cost on the expense item will be used. *Required if expenseItem is not specified
unitPrice           | Number | No* | Price per unit. If not specified, the price from the price list set on the customer will be used. If no price list is set, the price will be calculated from the cost and the 'Mark up on purchase price' on the customer. If 'Mark up on purchase price' is 0, the price will be set to the expense item price. *Required if expenseItem is not specified
discountPercent     | Number | No* | Discount percent on the unit price. *Required if expenseItem is not specified
taxPercent          | Number | No* | Tax percent on the unit price. *Required if expenseItem is not specified
timestamp           | String | No  | Time stamp of expense
description         | String | No  | Description of the expense
isInvoiceable       | Boolean | No | Is the expense invoiceable?
doReimburse         | Boolean | No | Is the expense an own expense?

## Update an Expense

```shell
  curl -X PUT "https://app.seventime.se/api/2/expenses/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fbe684416625651d7f43257","modifiedByUser":"5f48eb3e65d7ee4942c46eeb","user":"51203146506d961c030791801"}'
```

```javascript
let jsonData = {
  _id: '5fbe684416625651d7f43257',
  modifiedByUser: '5f48eb3e65d7ee4942c46eeb',
  user: '51203146506d961c030791801'
};

let options = {
  url: 'https://app.seventime.se/api/2/expenses',
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
    console.log("Expense updated: _id: " + body._id);
  } else {
    console.error("ERROR! Unable to update expense: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "isInvoiceable": true,
  "_id": "5fbe684416625651d7f43257",
  "timestamp": "2020-11-25T14:20:52.129Z",
  "documents": [],
  "createDate": "2020-11-25T14:20:52.129Z",
  "bundledArticles": [],
  "customFields": [],
  "systemAccount": "5112826056d961c030000001",
  "numberOfItems": 1,
  "user": "51203146506d961c030791801",
  "userName": "Tommy Hellström",
  "expenseItem": "5de78aed1332719192362bed",
  "articleNumber": "575733",
  "name": "10-pack Reaktionsbollar",
  "description": "Skivhantel av järn",
  "distributor": "573c52cdf609f5692351914b",
  "distributorName": "Lev 4",
  "unit": "St",
  "unitCost": 319,
  "unitTaxPercent": 25,
  "unitPrice": 426.66,
  "unitPriceAfterDiscount": 426.66,
  "discountPercent": 0,
  "unitTax": 106.665,
  "unitPriceInclTax": 533.325,
  "totalTaxAmount": 106.665,
  "totalAmount": 426.66,
  "totalAmountAfterDiscount": 426.66,
  "totalCost": 319,
}
"Expense updated: _id: 5fbe684416625651d7f43257"
```

This endpoint updates an expense

### HTTP Request

`PUT https://app.seventime.se/api/2/expenses/`

### PUT Parameters
The table below shows the required fields. Other available fields can be found in the section 'Create an Expense'.


Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id            | String | Yes | Id of the expense
modifiedByUser | String | Yes | Id of the user who made the change
user           | String | Yes | Id of the user on the expense

## Delete an Expense

```shell
  curl -X DELETE "https://app.seventime.se/api/2/expenses/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fbe684416625651d7f43257","deletedByUser":"51203146506d961c030791801"}'
```

```javascript
let jsonData = {
  _id: "5fbe684416625651d7f43257",
  deletedByUser: '51203146506d961c030791801'
};

let options = {
  url: 'https://app.seventime.se/api/2/expenses',
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
    console.log("Expense deleted: _id: " + body._id);
  } else {
    console.error("ERROR! Unable to delete expense: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "_id": "5fbe684416625651d7f43257"
}
"Expense deleted: _id: 5fbe684416625651d7f43257"
```

This endpoint deletes an expense

### HTTP Request

`DELETE https://app.seventime.se/api/2/expenses/`

### DELETE Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                | String | Yes | Id of the expense
deletedByUser      | String | Yes | Id of the user who deleted the expense
