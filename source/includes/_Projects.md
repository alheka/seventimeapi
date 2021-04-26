# Projects

## Get Projects


```shell
curl "https://app.seventime.se/api/2/projects/?limit=10&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/projects/?limit=10&page=1";
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
    "totalResources": 397,
    "totalPages": 40,
    "currentPage": 7
  },
  "data": [
    {
      "_id": "5f924f4f533f102af78f95b6",
      "permissions": {
        "permUsers": [],
        "permRoles": [],
        "permissionFlag": 1
      },
      "tags": [],
      "name": "Från offert 20200811",
      "projectNumber": "3314",
      "projectStatus": 50,
      "projectStatusRef": "5c8739d3205457b98b9883d4",
      "projectType": null,
      "projectTypeName": null,
      "billingMethod": "FIXED_PRICE",
      "pricePerHour": 0,
      "fixedPrice": 0,
      "fixedPriceInvoiced": false,
      "fixedPriceLeftToInvoice": 0,
      "fixedPriceExpenseItem": null,
      "timeCategoryPriceList": null,
      "estimatedTime": 0,
      "recurringBudgetType": 10,
      "recurringBudget": {
        "budgetTime": 0,
        "budgetAmount": 0,
        "budgetType": 10
      },
      "resultUnit": null,
      "resultUnitName": "",
      "customer": "5763e05bcddce98e3b00004b",
      "customerName": "Hellapps",
      "contactPerson": null,
      "contactPersonName": null,
      "projectLeader": null,
      "projectLeaderName": null,
      "quote": "5b110ea19b27f5ef3f00007b",
      "quoteNumber": "1058",
      "department": null,
      "departmentName": "",
      "marking": "",
      "yourOrderNumber": "1058",
      "deliveryAddress": {
        "name": "",
        "address": "",
        "address2": "",
        "zipCode": "",
        "city": "",
        "country": "",
        "phone": ""
      },
      "invoiceStatus": 0,
      "notes": "",
      "documents": [],
      "startDate": null,
      "endDate": null,
      "budget": {
        "typeOfBenefitCalc": 1,
        "benefits": [],
        "benefitTotal": 0,
        "typeOfCostCalc": 1,
        "costs": [],
        "costTotal": 0
      },
      "budgetCalculation": {
        "invoiceItems": [],
        "totalBenefitAmount": 0,
        "totalCostAmount": 0
      },
      "enableConstructionDiary": false,
      "enablePaymentPlans": false,
      "timeCategoryItems": [],
      "expenseItemItems": [],
      "staffLedger": {
        "workPlaceIDNumber": "",
        "developerName": "",
        "developerOrgNumber": ""
      },
      "projectTimeNotification": {
        "sent": false,
        "notifyAtPercent": 0
      },
      "workRuleStartOfDay": null,
      "workRuleEndOfDay": null,
      "timeLogRegistrationMethods": [],
      "timeShouldNotBeWorkTime": false,
      "enablePortalAccess": false,
      "projectResources": [],
      "checkLists": [],
      "color": "FAFAFA",
      "isActive": true,
      "comments": [],
      "customFields": [
        {
          "_id": "5f326f50433f102ff77f95d7",
          "fieldId": "5c0e7342ce9a647150000083",
          "value": "5c0e7342ce9a647150000085"
        }
      ],
      "createdDate": "2020-08-11T10:13:36.001Z",
      "modifiedDate": "2020-08-11T10:13:36.002Z",
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves projects.

### HTTP Request

`GET https://app.seventime.se/api/2/projects`

### Query Parameters

E.g. `https://app.seventime.se/api/2/projects/?projectNumber=3314`

Parameter | Default | Description
--------- | ------- | -----------
name            |  | If specified, projects that match the parameter will be included.
projectNumber   |  | If specified, projects that match the parameter will be included.
sortBy          |  | If specified, a sort will be made on the specified parameter
sortDirection   |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending




## Get a specific project

```shell
curl "https://app.seventime.se/api/2/projects/5f924f4f533f102af78f95b6" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/projects/5f924f4f533f102af78f95b6";
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
    "recurringBudget": {
      "budgetTime": 0,
      "budgetAmount": 0,
      "budgetType": 10
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
    "budget": {
      "typeOfBenefitCalc": 1,
      "benefits": [],
      "benefitTotal": 0,
      "typeOfCostCalc": 1,
      "costs": [],
      "costTotal": 0
    },
    "budgetCalculation": {
      "invoiceItems": [],
      "totalBenefitAmount": 0,
      "totalCostAmount": 0
    },
    "permissions": {
      "permUsers": [],
      "permRoles": [],
      "permDepartments": [],
      "permissionFlag": 1
    },
    "staffLedger": {
      "workPlaceIDNumber": "",
      "developerName": "",
      "developerOrgNumber": ""
    },
    "projectTimeNotification": {
      "sent": false,
      "notifyAtPercent": 0
    },
    "tags": [],
    "_id": "5f326f4f433f102ff77f95d6",
    "name": "Från offert 20200811",
    "projectNumber": "3314",
    "projectStatus": 50,
    "projectStatusRef": "5c8639c3205457b88d9897b2",
    "projectType": null,
    "projectTypeName": null,
    "billingMethod": "FIXED_PRICE",
    "pricePerHour": 0,
    "fixedPrice": 0,
    "fixedPriceInvoiced": false,
    "fixedPriceLeftToInvoice": 0,
    "fixedPriceExpenseItem": null,
    "timeCategoryPriceList": null,
    "estimatedTime": 0,
    "recurringBudgetType": 10,
    "resultUnit": null,
    "resultUnitName": "",
    "customer": "5763e05bcddce98e3b00004b",
    "customerName": "Hellapps",
    "contactPerson": null,
    "contactPersonName": null,
    "projectLeader": null,
    "projectLeaderName": null,
    "quote": "5b110ea19b27f5ef3f00007b",
    "quoteNumber": "1058",
    "department": null,
    "departmentName": "",
    "marking": "",
    "yourOrderNumber": "1058",
    "invoiceStatus": 0,
    "notes": "",
    "documents": [],
    "startDate": null,
    "endDate": null,
    "enableConstructionDiary": false,
    "enablePaymentPlans": false,
    "timeCategoryItems": [],
    "expenseItemItems": [],
    "workRuleStartOfDay": null,
    "workRuleEndOfDay": null,
    "timeLogRegistrationMethods": [],
    "timeShouldNotBeWorkTime": false,
    "enablePortalAccess": false,
    "projectResources": [],
    "checkLists": [],
    "color": "FAFAFA",
    "isActive": true,
    "comments": [],
    "customFields": [
      {
        "_id": "5f326f50433f102ff77f95d7",
        "fieldId": "5c0e7342ce9a647150000083",
        "value": "5c0e7342ce9a647150000085"
      }
    ],
    "createdDate": "2020-08-11T10:13:36.001Z",
    "modifiedDate": "2020-08-11T10:13:36.002Z",
    "systemAccount": "5112826056d961c030000001",
  }
}
```

This endpoint retrieves a specific project.



### HTTP Request

`GET https://app.seventime.se/api/2/projects/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the project to retrieve

## Get Project statuses

```shell
curl "https://app.seventime.se/api/2/projectStatuses/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/projectStatuses/";
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
      "_id": "5c8639c4704957d88b9894b1",
      "statusName": "Avslutad",
      "color": "468847",
      "inProgressStatus": false,
      "closedStatus": true,
      "isActive": true
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves project statuses.



### HTTP Request

`GET https://app.seventime.se/api/2/projectStatuses/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get Project types

```shell
curl "https://app.seventime.se/api/2/projectTypes/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/projectTypes/";
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
      "_id": "5b276a908e0273b743607182",
      "projectTypeName": "Dev",
      "isActive": true,
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves project types.



### HTTP Request

`GET https://app.seventime.se/api/2/projectTypes/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get Project tags

```shell
curl "https://app.seventime.se/api/2/projectTags/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/projectTags/";
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
      "_id": "5fb2c736deb93b2713515684",
      "tagName": "Viktigt",
      "color": "673ab7"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves project tags.



### HTTP Request

`GET https://app.seventime.se/api/2/projectTags/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy        |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Create a Project
```shell
  curl -X POST "https://app.seventime.se/api/2/projects/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"createdByUser":"5f48eb3e65d7ee4942c46eeb","name":"App development"}' 
```

```javascript
const jsonData = {
  createdByUser: '5f48eb3e65d7ee4942c46eeb',
  name: 'App development',
};

const options = {
  url: 'https://app.seventime.se/api/2/projects',
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
    console.log("Project created: " + body.name + ", _id: " + body._id);
  } else {
    console.error("ERROR! Unable to create project: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
    "budget": { "benefits": [], "costs": [] },
    "budgetCalculation": { "invoiceItems": [] },
    "permissions": { "permUsers": [], "permRoles": [], "permDepartments": [] },
    "_id": "5fb3c92dd5472a243e9caa3b",
    "tags": [],
    "createdDate": "2020-11-17T12:59:25.109Z",
    "modifiedDate": "2020-11-17T12:59:25.109Z",
    "documents": [],
    "timeCategoryItems": [],
    "expenseItemItems": [],
    "timeLogRegistrationMethods": [],
    "projectResources": [],
    "checkLists": [],
    "comments": [],
    "customFields": [],
    "name": "App development",
    "projectNumber": "12345786" 
}
"Project created: App development, _id: 5fb3c92dd5472a243e9caa3b"
```

This endpoint creates a project.

### HTTP Request

`POST https://app.seventime.se/api/2/projects`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
createdByUser           | String | Yes | Id of the user who created the project
name                    | String | Yes | Name of the project
projectNumber           | Number | No  | Project number must be unique if specified. If not specified, it will be automatically assigned
projectStatusRef        | String | No  | Id of the status of the project
customer                | String | No  | Id of the customer of the project
contactPerson           | String | No  | Id of the contact person. This field requires that customer is specified and that the customer person belongs to that customer
invoiceStatus           | Number | No  | Invoice status of the project. See below for available statuses
projectLeader           | String | No  | Id of the user who should be the project leader
projectType             | String | No  | Id of the project type
department              | String | No  | Id of the department
startDate               | String | No  | Start date of the project in the format YYYY-MM-DD
endDate                 | String | No  | End date of the project in the format YYYY-MM-DD
notes                   | String | No  | Notes to be included in the project
resultUnit              | String | No  | Id of the result unit of the project
billingMethod           | String | No  | Billing method of the project. See below for available billing methods
pricePerHour            | Number | No* | Required if billingMethod is set to HOURLY
fixedPrice              | Number | No* | Required if billingMethod is set to FIXED_PRICE
timeCategoryPriceList   | String | No* | Required if billingMethod is set to PRICELIST
projectTags             | Array  | No  | Array containing ids of tags
marking                 | String | No  | Marking on project
yourOrderNumber         | String | No  | Your order number
deliveryAddress         | Object | No  | Contains attributes for delivery address. See below for details


**Invoice statuses for projects**

Code | Status
--------- | ----------- 
0  | None
5  | Not invoiceable
10 | Ready to be invoiced
20 | Partly invoiced
30 | Fully invoiced

**Billing methods for projects**

Code | Billing method
--------- | ----------- 
ACCORDING_TO_CUSTOMER   | This requires that the customer has a billing method set
HOURLY                  | Hourly price
PERUSER                 | The price will be set per user
HOURLY_PER_TIMECATEGORY | Price will be set according to time category
FIXED_PRICE             | Fixed price
PRICELIST               | Price will be set according to a price list



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

## Update a Project

```shell
  curl -X PUT "https://app.seventime.se/api/2/projects/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fb3c92dd5472a243e9caa3b","name":"App development","customer":"571f61330c7f498a2d0001a4","modifiedByUser":"51718241fdb708f37959127"}' 
```

```javascript
const jsonData = {
  _id: '5fb3c92dd5472a243e9caa3b',
  modifiedByUser: '51718241fdb708f37959127',
  name: 'App development',
  customer: '571f61330c7f498a2d0001a4'
};

const options = {
  url: 'https://app.seventime.se/api/2/projects',
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
    console.log("Project updated: " + body.name + ", _id: " + body._id);
  } else {
    console.error("ERROR! Unable to update project: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
    "budget": { "benefits": [], "costs": [] },
    "budgetCalculation": { "invoiceItems": [] },
    "permissions": { "permUsers": [], "permRoles": [], "permDepartments": [] },
    "_id": "5fb3c92dd5472a243e9caa3b",
    "tags": [],
    "createdDate": "2020-11-17T12:59:25.109Z",
    "modifiedDate": "2020-11-17T12:59:25.109Z",
    "documents": [],
    "timeCategoryItems": [],
    "expenseItemItems": [],
    "timeLogRegistrationMethods": [],
    "projectResources": [],
    "checkLists": [],
    "comments": [],
    "customFields": [],
    "name": "App development",
    "projectNumber": "12345786",
    "customer": "571f61330c7f498a2d0001a4",
    "customerName": "Hellapps AB"
}
"Project updated: App development, _id: 5fb3c92dd5472a243e9caa3b"
```

This endpoint updates a project.

### HTTP Request

`PUT https://app.seventime.se/api/2/projects/?name=App development&customer=571f61330c7f498a2d0001a4`

### PUT Parameters

The table below shows the required fields. Other available fields can be found in the section 'Create a Project'.

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                     | String | Yes | Id of the project
modifiedByUser          | String | Yes | Id of the user who made the change

<!---
## Delete a Project

```shell
  curl -X DELETE "https://app.seventime.se/api/2/projects/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fb3c92dd5472a243e9caa3b","deletedByUser":"51718241fdb708f379596193"}' 
```

```javascript
const jsonData = {
  _id: '5fb3c92dd5472a243e9caa3b',
  deletedByUser: '51718241fdb708f379596193'
};

const options = {
  url: 'https://app.seventime.se/api/2/projects',
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
    console.log("Project deleted: " + body.name + ", _id: " + body._id);
  } else {
    console.error("ERROR! Unable to delete project: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
    "_id": "5fb3c92dd5472a243e9caa3b",
    "name": "App development",
    "projectNumber": "12345786",
}
"Project deleted: App development, _id: 5fb3c92dd5472a243e9caa3b"
```

This endpoint deletes a project.

### HTTP Request

`DELETE https://app.seventime.se/api/2/projects/name=App development&customer=571f61330c7f498a2d0001a4`

### DELETE Parameters


Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                     | String | Yes | Id of the project
deletedByUser           | String | Yes | Id of the user who deleted the project

-->
