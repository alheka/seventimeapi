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

# Custom fields
## Get Custom fields

```shell
curl "https://app.seventime.se/api/2/customFields/" \
  -H "Client-Secret: thisismysecretkey"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/customFields/";
let options = {
  url: url,
  headers: {
    "Client-Secret": "thisismysecretkey"
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
      "_id": "58a678badc33073a42e02802",
      "isActive": true,
      "__v": 0,
      "quoteCategoryName": "Utbildning"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves custom fields.

### HTTP Request

`GET https://app.seventime.se/api/2/customFields/<entityType>`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
entityType                          |  | Number corresponding to entity type. See table below for available types.

**Entity types**

Code | Description
--------- | ----------- 
100   | Time log
200   | Work order
300   | Taks
400   | Invoice
500   | Project
600   | Expense
700   | Machine time log
800   | Driver journal
900   | Salary deviation
1000   | User
1100   | Customer
1200   | Absence
1300   | Work time absence
1400   | Quote
1500   | Machine
1600   | Object item
1700   | Customer signature
1800   | Supplement order
1900   | Construction diary
2000   | Checklist
2100   | Payment plan


