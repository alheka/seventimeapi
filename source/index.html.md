---
title: Seven Time API Reference


language_tabs: # must be one of https://git.io/vQNgJ
- shell
- javascript

toc_footers:
- <a href="https://seventime.se">Seven Time</a>

includes:
- errors
- Analytics
- CompanyInformation
- ContactPersons
- Customers
- CustomFields
- Departments
- Distributors
- Documents
- DriverJournals
- Expenses
- Invoices
- Machines
- MachineTimeLogs
- ObjectItems
- PriceLists
- Projects
- PurchaseOrders
- Quotes
- ResultUnits
- Statuses
- SupplementOrders
- SupplierInvoices
- Tasks
- TimeLogs
- Timer
- Users
- Vehicles
- WebhookSubscriptions
- WorkOrders
- WorkSchedules
- Zapier
- Changelog

search: true
---

# Introduction

Welcome to the Seven Time API! You can use our API to access Seven Time API endpoints.

You can view code examples for Shell and JavaScript in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

Changes in the API that can affect an integration are listed in the [Changelog](#changelog).

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
You must replace <code>thisismysecretkey</code> with your API key.
</aside>

Requests made with an OAuth access token (e.g. through the Seven Time MCP server) act as the connected user and follow the user's permissions in Seven Time. A user without the permission to see financial information doesn't get prices, costs, amounts, result units or cost accounts in the responses (quote costs follow the permission to see quote costs), these fields are ignored in POST and PUT requests, and analytics metrics for them return HTTP 403. API keys are not affected.

# Header fields
In addition to the 'Client-Secret', a few fields are required in the Header:

- Client-Secret - Required for all requests. A missing or invalid key returns HTTP 401.
- Content-type - Must be "application/json". This is enforced for all non-GET requests.
- Accept - Must be "application/json"

# Actions
The Seven Time API supports four different actions:

- get - used to retrieve data
- post - used to create new items, e.g. new customers, users, etc.
- put - used to update items, e.g. update an exisiting customer, user, etc.
- delete - used to delete items e.g. delete a supplier invoice.

# Pagination
Searches that returns a large number of results are paged due to performance reasons. 

These searches are limited by the parameter 'limit'. This parameter limits the number of results that will be returned. By default (if not specified, or if it isn't a number), this limit is set to 100 but can be set as low as 1 and as high as 500.

When the number of results exceed the given limit, the 'page' parameter can be used to retrieve different intervals in the data. By default (if not specified),
this value is set to 1.


## Example of 'limit' and 'page'
A search returns 490 results and the limit is set to 100. To get the first 100 results, the parameter 'page' is set to 1. To get the next 100 results, 'page' is set to 2, etc.

The data returned will be in the form of a JSON and contain a meta property where you will find information about the total number of results, number of pages and the current page.
The data property contains the information requested.

For time logs, expenses, invoices, machine time logs, driver journals, purchase orders and work orders, the count is capped at 2000 for performance reasons, and the meta property contains some additional fields:

- totalResources - the number of matching results, but never more than 2000
- totalResourcesIsExact - false if there are more than 2000 matching results. In that case totalPages is null
- hasMore - true if there are more results after the current page
- nextPage - the number of the next page, or null if there are no more results

Some of these endpoints (driver journals, expenses, machine time logs and purchase orders) return HTTP 422 if no filter is given.

User roles, user salary types, user skills, user work types and time categories are paged with 'limit' and 'page' like the lists above.

The other lists of types, tags and settings (project statuses, types and tags, work order types, tags and statuses, quote templates and categories, invoice tags, machine types, object item types, driver journal types, result units, distributor contact persons, documents, document lists, custom fields, work schedules and webhook subscriptions) are not limited. All results are returned on page 1, and 'limit' is ignored. A higher page returns an empty data array, so a client that pages until it gets no results stops after page 2. They contain the same meta property, with totalPages 1 (0 if there are no results).


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

## Paging with a cursor

Deep pages are slow, because the server still reads every result before the page. To fetch all records of a list, or all records changed since a point in time, use a cursor instead of `page`:

1. Call the list with `cursor=first` (and `limit`, `lastModified` and any other filters).
2. While `meta.hasMore` is true, call the list again with the same filters and `cursor` set to `meta.nextCursor` from the previous response.

With a cursor, the results are sorted on the time they were last changed (`updatedAt`, or `modifiedDate` for customers, projects, work orders and object items), oldest first, then on `_id`. A record that is changed while you page gets a later time and comes again on a later page; it is never missed. Records without that time are not included.

The cursor is an opaque string: don't build or change it, only send back the value you got. `cursor` can't be combined with `page`, `sortBy` or `sortDirection` (HTTP 400), and an invalid cursor returns HTTP 400 with `Invalid cursor`. `limit` works as without a cursor (at most 500).

With a cursor, the meta property only contains `limit`, `hasMore` and `nextCursor` (null on the last page), without counts.

The cursor works on the lists of contact persons, customers, departments, distributors, driver journals, expense items, expenses, invoices, machine time logs, machines, object items, price lists, projects, purchase orders, quotes, supplement orders, supplier invoices, tasks, time logs, timers, users, vehicles and work orders.

```json
{
  "meta": {
    "limit": 100,
    "hasMore": true,
    "nextCursor": "eyJ2IjoxLCJmIjoidXBkYXRlZEF0IiwidCI6IjIwMjYtMTEtMThUMTA6MTU6MDAuMTIzWiIsImlkIjoiNjQ1YTFiMmMzZDRlNWY2YTdiOGM5ZDBlIn0"
  },
  "data": [
    {
      // ...
    }
  ]
}
```

# Rate-limit
When the number of requests reach the rate limit the HTTP 429 (Too Many Requests) is returned.
The production limit is **4 requests per second**. This equals to a bit more than 200 requests per minute.

