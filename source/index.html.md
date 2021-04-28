---
title: Seven Time API Reference


language_tabs: # must be one of https://git.io/vQNgJ
- shell
- javascript

toc_footers:
- <a href="https://seventime.se">Seven Time</a>

includes:
- errors
- ContactPersons
- Customers
- Departments
- Distributors
- DriverJournals
- Expenses
- Invoices
- Machines
- MachineTimeLogs
- PriceLists
- Projects
- PurchaseOrders
- Quotes
- ResultUnits
- SupplementOrders
- SupplierInvoices
- TimeLogs
- Users
- Vehicles
- WorkOrders

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
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Send Client-Secret in the header. Sample with the request library */

let options = {
  headers: {
    "Client-Secret": "thisismysecretkey",
    "Content-Type": "application/json",
    "Accept": 'application/json'
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

# Header fields
In addition to the 'Client-Secret', a few fields are required in the Header:

- Content-type - Must be "application/json"
- Accept - Must be "application/json"

# Actions
The Seven Time API supports four different actions:

- get - used to retrieve data
- push - used to create new items, e.g. new customers, users, etc.
- put - used to update items, e.g. update an exisiting customer, user, etc.
- delete - used to delete items e.g. delete a supplier invoice.

# Pagination
Searches that returns a large number of results are paged due to performance reasons. 

These searches are limited by the parameter 'limit'. This parameter limits the number of results that will be returned. By default (if not specified), this limit is set to 100 but can be set as low as 1 and as high as 500.

When the number of results exceed the given limit, the 'page' parameter can be used to retrieve different intervals in the data. By default (if not specified),
this value is set to 1.


## Example of 'limit' and 'page'
A search returns 490 results and the limit is set to 100. To get the first 100 results, the parameter 'page' is set to 1. To get the next 100 results, 'page' is set to 2, etc.

The data returned will be in the form of a JSON and contain a meta property where you will find information about the total number of results, number of pages and the current page.
The data property contains the information requested.


```json
{
  "meta": {
    "totalResources": 490,
    "totalPages": 5,
    "currentPage": 2
  },
  "data": [
    {
      // ...
    },
    {
      // ...
    }
  ]
}
```

# Rate-limit
When the number of requests reach the rate limit the HTTP 429 (Too Many Requests) is returned.
The limit is **4 requests per second**. This equals to a bit more than 200 requests per minute.

