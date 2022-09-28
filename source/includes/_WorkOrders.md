# Work Orders
## Get Work Orders

```shell
curl "https://app.seventime.se/api/2/workOrders/?limit=10&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/workOrders/?limit=10&page1";
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
    "totalResources": 1772,
    "totalPages": 355,
    "currentPage": 34
  },
  "data": [
    {
      "_id": "5bae34dca878bd790d0498751",
      "workOrderNumber": 2901,
      "createdByUserName": "Anna Andersson",
      "createdByUser": "59312765ad961c0311358974",
      "statusRef": "587f3157c73c0f6d9c568741",
      "status": 100,
      "customerNumber": "511",
      "customerName": "Kund #1",
      "customer": "571f61330c7f498a269751242",
      "estimatedTime": 0,
      "endDate": "2017-10-12T16:00:00.000Z",
      "startDate": "2017-10-10T07:00:00.000Z",
      "description": "",
      "title": "AO1",
      "customFields": [],
      "tags": [],
      "workOrderUserWorkTypes": [],
      "workOrderUserSkills": [],
      "budgetCalculation": {
        "invoiceItems": []
      },
      "invoiceRows": [],
      "todoItems": [],
      "reminders": [],
      "checkLists": [],
      "documents": [],
      "locationCoordinates": [],
      "workAddress": {
        "useOtherAddress": false,
        "address": "",
        "zipCode": "",
        "city": ""
      },
      "comments": [],
      "partTimeResources": [],
      "machines": [],
      "users": [],
      "createDate": "2018-09-28T13:17:16.785Z"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves work orders.

### HTTP Request

`GET https://app.seventime.se/api/2/workOrders`

### Query Parameters

E.g. `https://app.seventime.se/api/2/workOrders/?workOrderNumber=5555`

Parameter | Default | Description
--------- | ------- | -----------
title           |  | If specified, work orders that match the parameter will be included.
workOrderNumber |  | If specified, work orders that match the parameter will be included.
project         |  | If specified, work orders that match the parameter will be included.
user            |  | If specified, work orders that match the parameter will be included.
customer        |  | If specified, work orders that match the parameter will be included.
lastModified    |  | If specified, work orders that has been modified since the specified timestamp will be included. Accepted formats: 'YYYY-MM-HH HH:MM', 'YYYY-MM-HH HH:MM:SS', 'YYYY-MM-HHTHH:MM', 'YYYY-MM-HHTHH:MM:SS'
sortBy          |  | If specified, a sort will be made on the specified parameter
sortDirection   |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending




## Get a specific Work order

```shell
curl "https://app.seventime.se/api/2/workOrders/5bae34dca878b5497748" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/workOrders/5bae34dca878b5497748";
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
    "workAddress": {
      "useOtherAddress": false,
      "address": "",
      "zipCode": "",
      "city": ""
    },
    "budgetCalculation": {
      "invoiceItems": []
    },
    "locationCoordinates": [],
    "tags": [],
    "_id": "5bae34dca878b5497748",
    "workOrderNumber": 2901,
    "createdByUserName": "Anna Andersson",
    "createdByUser": "59312765ad961c0365978421",
    "statusRef": "587f3157c73c0f6d9125897451",
    "status": 100,
    "customerNumber": "511",
    "customerName": "Kund #1",
    "customer": "571f61330c7f498a216975841",
    "estimatedTime": 0,
    "endDate": "2017-10-12T16:00:00.000Z",
    "startDate": "2017-10-10T07:00:00.000Z",
    "description": "",
    "title": "AO1",
    "customFields": [],
    "workOrderUserWorkTypes": [],
    "workOrderUserSkills": [],
    "invoiceRows": [],
    "todoItems": [],
    "reminders": [],
    "checkLists": [],
    "documents": [],
    "comments": [],
    "partTimeResources": [],
    "machines": [],
    "users": [],
    "createDate": "2018-09-28T13:17:16.785Z",
    "relations": []
  }
}
```

This endpoint retrieves a specific work order.



### HTTP Request

`GET https://app.seventime.se/api/2/workOrders/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the work order to retrieve

## Get work order types

```shell
curl "https://app.seventime.se/api/2/workOrderTypes/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/workOrderTypes/";
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
      "_id": "58263d936a17605a25689741",
      "isActive": true,
      "workOrderTypeName": "Extra",
      "color": "f44336"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves work order types.



### HTTP Request

`GET https://app.seventime.se/api/2/workOrderTypes/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy          |  | If specified, a sort will be made on the specified parameter
sortDirection   |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get work order tags

```shell
curl "https://app.seventime.se/api/2/workOrderTags/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/workOrderTags/";
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
      "_id": "5df3a401f0690d1db659741",
      "tagName": "1",
      "color": "FAFAFA"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves work order tags.



### HTTP Request

`GET https://app.seventime.se/api/2/workOrderTags/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy        |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get Work order statuses

```shell
curl "https://app.seventime.se/api/2/workOrderStatuses/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/workOrderStatuses/";
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
      "_id": "582f7cabd16fdb974185235",
      "statusName": "Ej planerad",
      "color": "FF5722",
      "inProgressStatus": false,
      "closedStatus": false,
      "isActive": true,
      "plannedStatus": false
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves work order statuses.



### HTTP Request

`GET https://app.seventime.se/api/2/workOrderStatuses/`

### URL Parameters

No parameters

## Create a Work order
```shell
curl -X POST "https://app.seventime.se/api/2/workOrders/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"title":"Support","customer":"571f61330c7f49451685","createdByUser":"5912626016d971c03069712"}' 
```

```javascript
let jsonData = {
  title: 'Support',
  customer: '571f61330c7f49451685',
  createdByUser: '5912626016d971c03069712'
};

let options = {
  url: 'https://app.seventime.se/api/2/workOrders',
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
    console.error("ERROR! Unable to create work order: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
    "title": "Support"
    "workOrderNumber": 4908,       
    "description": "",   
    "locationCoordinates": [],
    "tags": [],
    "_id": "5fb8517e1bcaad1cd6987451",
    "createDate": "2020-11-16T10:15:42.216Z",
    "users": [],
    "machines": [],
    "partTimeResources": [],
    "comments": [],
    "documents": [],
    "checkLists": [],
    "reminders": [],
    "todoItems": [],
    "invoiceRows": [],
    "workOrderUserSkills": [],
    "workOrderUserWorkTypes": [],
    "customFields": [],
    "relations": [],
    "estimatedTime": 0, 
    "marking": "",
    "yourOrderNumber": "",
    "customerName": "Company AB",
    "customer": "571f61330c7f498a64978511",
    "color": "FF5722",
    "status": 500,
    "statusRef": "587f7dadd10fbbe338000055",
    "createdByUser": "5912626016d971c03069712",
    "createdByUserName": "Anna Andersson",
}
```

This endpoint creates a work order.

### HTTP Request

`POST https://app.seventime.se/api/2/workOrders/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
title               | String | Yes | Title of the work order
customer            | String | Yes | Customer id for the customer who the work order should belong to
createdByUser       | String | Yes | Id of the user who created the work order
statusRef           | String | No | Id of the status of the work order.
Project             | String | No | Project id for the project which the work order should belong to
startDate           | String | No | Start date for the work order. The format must be YYYY-MM-DD HH:MM
endDate             | String | No | End date for the work order. The format must be YYYY-MM-DD HH:MM
currentOwner        | String | No | Id of the user who is the current owner of the work order
users               | Array  | No | Array containing the ids of users who are working full time on the work order
machines            | Array  | No | Array containing the ids of the machines which are working full time on the work order
estimatedTime       | Number | No | Estimated time required to finish the work order
contactPerson       | String | No | Id of the contact person
workOrderType       | String | No | Id of the work order type
department          | String | No | Id of the department
workLeader          | String | No | Id of the work leader
description         | String | No | Description of the work order
color               | String | No | Color of the work order, only used if "How to set color" is 'Manually' in settings. See below for available colors
invoiceStatus       | Number | No | Invoice status of the work order. See below for available statuses
billingMethod       | String | No | Billing method of work order. See below for available billing methods
fixedPrice          | Number | No* | *Only if Billing method is set to FIXED_PRICE
isSupplementOrder   | Boolean | No | Should the work order be set as supplement order?
workAddress         | Object | No | Contains attributes for work address. If not specified, the customers address will be set as work address. See below for details
enablePortalAccess  | Boolean | No | Should the work order be available in the customer portal?
allowRegistrationOfTimes     | Boolean | No | Should it be possible to register times on the work order?
allowRegistrationOfExpenses  | Boolean | No | Should it be possible to register expenses on the work order?
marking             | String | No | Marking on the work order
yourOrderNumber     | String | No | Your order number of the work order

**Colors for work orders**

<span style="width: 16px; height: 16px; background: #9c27b0;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 9c27b0 <br>
<span style="width: 16px; height: 16px; background: #673ab7;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 673ab7 <br>
<span style="width: 16px; height: 16px; background: #7C4DFF;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 7C4DFF <br>
<span style="width: 16px; height: 16px; background: #3F51B5;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 3F51B5 <br>
<span style="width: 16px; height: 16px; background: #3a87ad;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 3a87ad <br>

<span style="width: 16px; height: 16px; background: #2196F3;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 2196F3 <br>
<span style="width: 16px; height: 16px; background: #03A9F4;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 03A9F4 <br>
<span style="width: 16px; height: 16px; background: #00BCD4;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 00BCD4 <br>
<span style="width: 16px; height: 16px; background: #009688;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 009688 <br>
<span style="width: 16px; height: 16px; background: #468847;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 468847 <br>

<span style="width: 16px; height: 16px; background: #4CAF50;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 4CAF50 <br>
<span style="width: 16px; height: 16px; background: #8BC34A;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 8BC34A <br>
<span style="width: 16px; height: 16px; background: #CDDC39;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - CDDC39 <br>
<span style="width: 16px; height: 16px; background: #FF9800;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - FF9800 <br>
<span style="width: 16px; height: 16px; background: #FF5722;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - FF5722 <br>

<span style="width: 16px; height: 16px; background: #f44336;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - f44336 <br>
<span style="width: 16px; height: 16px; background: #e91e63;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - e91e63 <br>
<span style="width: 16px; height: 16px; background: #795548;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 795548 <br>
<span style="width: 16px; height: 16px; background: #5D4037;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 5D4037 <br>
<span style="width: 16px; height: 16px; background: #999999;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 999999 <br>

<span style="width: 16px; height: 16px; background: #666666;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 666666 <br>
<span style="width: 16px; height: 16px; background: #333333;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 333333 <br>
<span style="width: 16px; height: 16px; background: #000000;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - 000000 <br>
<span style="width: 16px; height: 16px; background: #FAFAFA;">&nbsp;&nbsp;&nbsp;&nbsp;</span> - FAFAFA <br>


**Invoice statuses for work orders**

Code | Status
--------- | ----------- 
0  | None
5  | Not invoiceable
10 | Ready to be invoiced
20 | Partly invoiced
30 | Fully invoiced

**Billing methods for work orders**

Code | Billing method
--------- | ----------- 
RUNNING             | Running price
FIXED_PRICE         | Fixed price
ACCORDING_TO_QUOTE  | Price will be set according to quote



**Attributes for workAddress**

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
useOtherAddress             | Boolean | Yes | Should an alternative work address be used?
name                        | String  | No  | Used if useSeparateBillingAddress is true
address                     | String  | No  | Used if useSeparateBillingAddress is true
address2                    | String  | No  | Used if useSeparateBillingAddress is true
zipCode                     | String  | No  | Used if useSeparateBillingAddress is true
city                        | String  | No  | Used if useSeparateBillingAddress is true
country                     | String  | No  | Used if useSeparateBillingAddress is true, given as a country code (E.g. SE for Sweden)
phone                       | String  | No  | Used if useSeparateBillingAddress is true

## Update a Work order


```shell
curl -X PUT "https://app.seventime.se/api/2/workOrders/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fb8517e1bcaad1cd69875412","modifiedByUser":"5f48eb3e65d7e987513654","title":"Construction work"}' 
```

```javascript
let jsonData = {
  _id: '5fb8517e1bcaad1cd69875412',
  modifiedByUser: '5f48eb3e65d7e987513654',
  title: 'Construction work'
};

let options = {
  url: 'https://app.seventime.se/api/2/workOrders',
  json: jsonData,
  headers: {
    "Client-Secret": "thisismysecretkey",
    'Content-Type': 'application/json',
    'Accept': 'application/json'
  }
};

request.put(options, function (error, response, body) {
  if (!error && response.statusCode === 200) {
    console.log(body);
    console.log("Work Order updated: " + body.title + ", _id: " + body._id);
  } else {
    console.error("ERROR! Unable to update work order: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "runningInvoiceSettings":
   { 
     "oneRowText": "Arbetsorder #{{workOrderNumber}} {{workOrderTitle}}",
     "timeLogMachineSupplement": "nothing",
     "timeLogCustomField": "nothing",
     "includeDescription": true,
     "includeDateRange": false,
     "includeDate": true,
     "includeUser": true,
     "machineFromTimeLog": false,
     "includeCategory": true,
     "includeTask": false,
     "includeWorkOrder": false,
     "includeProject": false,
     "formatType": "detailedFormat" 
   },
  "budgetCalculation": { "invoiceItems": [] },
  "locationCoordinates": [],
  "tags": [],
  "_id": "5fb8517e1bcaad1cd26497821",
  "createDate": "2020-12-14T14:39:40.951Z",
  "users": [],
  "machines": [],
  "partTimeResources": [],
  "comments": [],
  "documents": [],
  "checkLists": [],
  "reminders":
   [ { "_id": "5321507b60913236597511",
       "reminderTimeType": 4,
       "reminderTimeValue": 10,
       "reminderType": 1,
       "itemId": "0.2819101621862501" } ],
  "todoItems": [],
  "invoiceRows": [],
  "workOrderUserSkills": [],
  "workOrderUserWorkTypes": [],
  "customFields": [],
  "relations": [],
  "title": "Construction work",
  "estimatedTime": 0,
  "description": "",
  "marking": "",
  "yourOrderNumber": "",
  "customerName": "Company",
  "customer": "571f61330c7f498a2d987841",
  "color": "FAFAFA",
  "status": 100,
  "statusRef": "582f7cabd16fdbe985147",
  "createdByUser": "5f48eb3e65d7ee987854125",
  "createdByUserName": "Anna Andersson",
  "workOrderNumber": 4942,
  "completedByUser": null,
  "completedByUserName": "",
  "completedDate": null,
  "inProgressByUser": null,
  "inProgressByUserName": "",
  "inProgressDate": null,
  "modifiedByUser": "5f48eb3e65d7e987513587",
  "modifiedByUserName": "Anna Andersson",
  "modifiedDate": "2020-12-14T14:43:29.158Z" 
}
"Work Order updated: Construction work, _id: 5fb8517e1bcaad1cd26497821"
```

This endpoint updates a work order.

### HTTP Request

`PUT https://app.seventime.se/api/2/workOrders/`

### PUT Parameters
The table below shows the required fields. Other available fields can be found in the section 'Create a Work Order'.

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id               | String | Yes | Id of the work order
modifiedByUser    | String | Yes | Id of the user who updated the work order

<!---
## Delete a Work order
```shell
curl -X DELETE "https://app.seventime.se/api/2/workOrders" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"id":"5fb8517e1bcaad1cd26497821","deletedByUser":"5f48eb3e65d7ee45497521"}' 
```

```javascript
let jsonData = {
  _id: '5fb8517e1bcaad1cd26497821',
  deletedByUser: '5f48eb3e65d7ee45497521'
};

let options = {
  url: 'https://app.seventime.se/api/2/workOrders',
  json: jsonData,
  headers: {
    "Client-Secret": "thisismysecretkey",
    'Content-Type': 'application/json',
    'Accept': 'application/json'
  }
};

request.delete(options, function (error, response, body) {
  if (!error && response.statusCode === 200) {
    console.log(body);
    console.log("Work Order deleted: " + body.title + ", _id: " + body._id);
  } else {
    console.error("ERROR! Unable to delete work order: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "_id": "5fb8517e1bcaad1cd26497821",
  "title": "Construction work",
  "workOrderNumber": 4942,
}
"Work Order updated: Construction work, _id: 5fb8517e1bcaad1cd26497821"
```

This endpoint deletes a work order.

### HTTP Request

`DELETE https://app.seventime.se/api/2/workOrders/`

### DELETE Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id               | String | Yes | Id of the work order
deletedByUser    | String | Yes | Id of the user who deleted the work order
-->
