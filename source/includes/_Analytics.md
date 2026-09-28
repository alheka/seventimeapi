# Analytics

The analytics endpoints return aggregated data, e.g. hours per customer and month or invoiced amount per project, without having to fetch and sum every single object.

All analytics endpoints work the same way. You send a `POST` request with a JSON body that specifies a date range, what to group by and which metrics to calculate. The available groupings, metrics, date fields and filters differ per resource and are listed under each endpoint below.

## Get Time Log Analytics

```shell
curl -X POST "https://app.seventime.se/api/2/analytics/timeLogs" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"fromDate":"2024-01-01","toDate":"2024-03-31","groupBy":["customer","month"],"metrics":["hours","revenue"],"sort":{"metric":"hours","direction":"desc"},"limit":20}'
```

```javascript
let jsonData = {
  fromDate: '2024-01-01',
  toDate: '2024-03-31',
  groupBy: ['customer', 'month'],
  metrics: ['hours', 'revenue'],
  sort: {
    metric: 'hours',
    direction: 'desc'
  },
  limit: 20
};

let options = {
  url: 'https://app.seventime.se/api/2/analytics/timeLogs',
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
    console.error("ERROR! Unable to get time log analytics: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "group": {
        "customer": "5bae34dca878b5497748",
        "customerName": "Kund AB",
        "year": 2024,
        "month": 2
      },
      "hours": 124.5,
      "revenue": 99600
    },
    {
      "group": {
        "customer": "5bae34dca878b5497749",
        "customerName": "Bygg AB",
        "year": 2024,
        "month": 1
      },
      "hours": 88,
      "revenue": 70400
    }
  ],
  "meta": {
    "groupBy": ["customer", "month"],
    "dateField": "timestamp",
    "groupCount": 2,
    "limit": 20,
    "currentPage": 1,
    "hasMore": false,
    "nextPage": null
  }
}
```

This endpoint returns aggregated time logs.

### HTTP Request

`POST https://app.seventime.se/api/2/analytics/timeLogs`

### POST Parameters

These parameters are the same for all analytics endpoints.

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
fromDate  | String | Yes | Start of the date range, in the format 'YYYY-MM-DD'
toDate    | String | Yes | End of the date range (inclusive), in the format 'YYYY-MM-DD'. The date range can be at most 5 years
groupBy   | String or Array | Yes | What to group by. Either a single value, e.g. `"customer"`, or an array of up to two different values, e.g. `["customer", "month"]`
metrics   | Array  | Yes | The metrics to calculate for each group, e.g. `["hours", "revenue"]`
dateField | String | No  | The date field that `fromDate`/`toDate` and the date groupings (`day`, `week`, `month`, `year`) are based on. Defaults to the first value listed for each endpoint
filters   | Object | No  | Filters that limit which objects are included. See each endpoint for available filters
sort      | Object | No  | `metric`: one of the requested metrics, defaults to the first one. `direction`: "asc" or "desc", defaults to "desc"
limit     | Number | No  | Number of groups per page. Default 20, maximum 500
page      | Number | No  | Page number. Default 1

### Response

Each object in `data` contains `group`, which describes the group, and one field per requested metric. `group` contains the ids and names for the requested groupings:

groupBy | Fields in group
------- | ---------------
day     | `date` ('YYYY-MM-DD')
week    | `year`, `week` (ISO week)
month   | `year`, `month`
year    | `year`
status  | `status` (status code)

Other groupings return the id of the object together with its name, e.g. `customer` and `customerName`.

Use `meta.hasMore` and `meta.nextPage` to fetch the next page.

Invalid parameters, e.g. an unknown metric or grouping, a missing date range or an invalid id in `filters`, return HTTP status 400 with an `errorMessage` describing the error.

### Time logs

Option | Values
------ | ------
dateField | `timestamp`, `createDate`
groupBy   | `customer`, `project`, `user`, `activity` (time category), `day`, `week`, `month`, `year`
metrics   | `hours`, `billableHours`, `nonBillableHours`, `cost`, `revenue`, `logCount`

Filter | Description
------ | -----------
customerId | Id of a customer
projectId  | Id of a project
userId     | Id of a user
activityId | Id of a time category

## Get Invoice Analytics

```shell
curl -X POST "https://app.seventime.se/api/2/analytics/invoices" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"fromDate":"2024-01-01","toDate":"2024-12-31","groupBy":"month","metrics":["netAmount","invoiceCount"]}'
```

This endpoint returns aggregated invoices. See [Get Time Log Analytics](#get-time-log-analytics) for the request and response format.

Draft, obliterated and customer loss invoices (status 1, 4 and 7) are excluded unless `filters.status` is specified. Credit invoices are subtracted from the amounts.

### HTTP Request

`POST https://app.seventime.se/api/2/analytics/invoices`

Option | Values
------ | ------
dateField | `invoiceDate`, `sentDate`, `createDate`
groupBy   | `customer`, `project`, `month`, `year`, `status`
metrics   | `netAmount` (excl. tax), `grossAmount` (incl. tax), `taxAmount`, `invoiceCount`

Filter | Description
------ | -----------
customerId | Id of a customer
projectId  | Id of a project
status     | Invoice status, 1-7. Only invoices with this status are included

## Get Expense Analytics

```shell
curl -X POST "https://app.seventime.se/api/2/analytics/expenses" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"fromDate":"2024-01-01","toDate":"2024-12-31","groupBy":"expenseItem","metrics":["quantity","revenue"]}'
```

This endpoint returns aggregated expenses. See [Get Time Log Analytics](#get-time-log-analytics) for the request and response format.

### HTTP Request

`POST https://app.seventime.se/api/2/analytics/expenses`

Option | Values
------ | ------
dateField | `timestamp`, `createDate`
groupBy   | `customer`, `project`, `user`, `expenseItem`, `day`, `week`, `month`, `year`
metrics   | `cost`, `revenue`, `quantity`, `expenseCount`

Filter | Description
------ | -----------
customerId    | Id of a customer
projectId     | Id of a project
userId        | Id of a user
expenseItemId | Id of an expense item

## Get Machine Time Log Analytics

```shell
curl -X POST "https://app.seventime.se/api/2/analytics/machineTimeLogs" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"fromDate":"2024-01-01","toDate":"2024-12-31","groupBy":["machine","month"],"metrics":["hours"]}'
```

This endpoint returns aggregated machine time logs. See [Get Time Log Analytics](#get-time-log-analytics) for the request and response format.

### HTTP Request

`POST https://app.seventime.se/api/2/analytics/machineTimeLogs`

Option | Values
------ | ------
dateField | `timestamp`, `createDate`
groupBy   | `machine`, `customer`, `project`, `user`, `day`, `week`, `month`, `year`
metrics   | `hours`, `billableHours`, `nonBillableHours`, `cost`, `revenue`, `logCount`

Filter | Description
------ | -----------
customerId | Id of a customer
projectId  | Id of a project
userId     | Id of a user
machineId  | Id of a machine

## Get Driver Journal Analytics

```shell
curl -X POST "https://app.seventime.se/api/2/analytics/driverJournals" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"fromDate":"2024-01-01","toDate":"2024-12-31","groupBy":"vehicle","metrics":["distance","tripCount"]}'
```

This endpoint returns aggregated driver journals. See [Get Time Log Analytics](#get-time-log-analytics) for the request and response format.

### HTTP Request

`POST https://app.seventime.se/api/2/analytics/driverJournals`

Option | Values
------ | ------
dateField | `timestamp`, `createDate`
groupBy   | `user`, `customer`, `project`, `vehicle`, `day`, `week`, `month`, `year`
metrics   | `distance`, `cost`, `revenue`, `tripCount`

Filter | Description
------ | -----------
customerId | Id of a customer
projectId  | Id of a project
userId     | Id of a user
vehicleId  | Id of a vehicle

## Get Supplier Invoice Analytics

```shell
curl -X POST "https://app.seventime.se/api/2/analytics/supplierInvoices" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"fromDate":"2024-01-01","toDate":"2024-12-31","groupBy":"distributor","metrics":["netAmount"]}'
```

This endpoint returns aggregated supplier invoices. See [Get Time Log Analytics](#get-time-log-analytics) for the request and response format.

Obliterated supplier invoices (status 35) are excluded unless `filters.status` is specified. Credit invoices are subtracted from the amounts.

### HTTP Request

`POST https://app.seventime.se/api/2/analytics/supplierInvoices`

Option | Values
------ | ------
dateField | `invoiceDate`, `dueDate`, `createDate`
groupBy   | `customer`, `project`, `distributor`, `month`, `year`, `status`
metrics   | `netAmount` (excl. tax), `grossAmount` (incl. tax), `taxAmount`, `invoiceCount`

Filter | Description
------ | -----------
customerId    | Id of a customer
projectId     | Id of a project
distributorId | Id of a distributor
status        | Supplier invoice status: 1 (Registered), 5 (Draft), 7 (Sent), 10 (Invoiced), 15 (Attest pending), 35 (Obliterated) or 50 (Paused)

## Get Work Order Analytics

```shell
curl -X POST "https://app.seventime.se/api/2/analytics/workOrders" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"fromDate":"2024-01-01","toDate":"2024-12-31","groupBy":["workOrderType","month"],"metrics":["workOrderCount"]}'
```

This endpoint returns the number of work orders. See [Get Time Log Analytics](#get-time-log-analytics) for the request and response format.

### HTTP Request

`POST https://app.seventime.se/api/2/analytics/workOrders`

Option | Values
------ | ------
dateField | `createDate`, `startDate`
groupBy   | `customer`, `project`, `department`, `workOrderType`, `status`, `month`, `year`
metrics   | `workOrderCount`

Filter | Description
------ | -----------
customerId      | Id of a customer
projectId       | Id of a project
departmentId    | Id of a department
workOrderTypeId | Id of a work order type
status          | Work order status code

## Get Purchase Order Analytics

```shell
curl -X POST "https://app.seventime.se/api/2/analytics/purchaseOrders" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"fromDate":"2024-01-01","toDate":"2024-12-31","groupBy":"distributor","metrics":["netAmount","orderCount"]}'
```

This endpoint returns aggregated purchase orders. See [Get Time Log Analytics](#get-time-log-analytics) for the request and response format.

Draft and obliterated purchase orders (status 1 and 3) are excluded unless `filters.status` is specified.

### HTTP Request

`POST https://app.seventime.se/api/2/analytics/purchaseOrders`

Option | Values
------ | ------
dateField | `purchaseOrderDate`, `createDate`
groupBy   | `distributor`, `project`, `status`, `month`, `year`
metrics   | `netAmount` (excl. tax), `grossAmount` (incl. tax), `cost`, `orderCount`

Filter | Description
------ | -----------
distributorId | Id of a distributor
projectId     | Id of a project
status        | Purchase order status: 1 (Draft), 2 (Sent), 3 (Obliterated), 4 (Confirmed) or 10 (Delivered)

## Get Quote Analytics

```shell
curl -X POST "https://app.seventime.se/api/2/analytics/quotes" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"fromDate":"2024-01-01","toDate":"2024-12-31","groupBy":["month","status"],"metrics":["quoteCount","quotedAmount"]}'
```

This endpoint returns aggregated quotes. See [Get Time Log Analytics](#get-time-log-analytics) for the request and response format.

Draft quotes (status 1) are excluded unless `filters.status` is specified. To calculate e.g. a win rate, group by `["month", "status"]` and compare `quoteCount` per status.

### HTTP Request

`POST https://app.seventime.se/api/2/analytics/quotes`

Option | Values
------ | ------
dateField | `quoteDate`, `sentDate`, `createDate`
groupBy   | `customer`, `project`, `quoteCategory`, `status`, `month`, `year`
metrics   | `quotedAmount` (excl. tax), `quotedAmountInclTax`, `quoteCount`

Filter | Description
------ | -----------
customerId      | Id of a customer
projectId       | Id of a project
quoteCategoryId | Id of a quote category
status          | Quote status: 1 (Draft), 2 (Sent), 3 (Accepted), 4 (Not accepted) or 10 (Opportunity)

## Get Task Analytics

```shell
curl -X POST "https://app.seventime.se/api/2/analytics/tasks" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"fromDate":"2024-01-01","toDate":"2024-12-31","groupBy":["user","completed"],"metrics":["taskCount"]}'
```

This endpoint returns the number of tasks. See [Get Time Log Analytics](#get-time-log-analytics) for the request and response format.

### HTTP Request

`POST https://app.seventime.se/api/2/analytics/tasks`

Option | Values
------ | ------
dateField | `createDate`, `dueDate`, `startDate`, `completedDate`
groupBy   | `user`, `customer`, `project`, `completed`, `month`, `year`
metrics   | `taskCount`

Filter | Description
------ | -----------
customerId | Id of a customer
projectId  | Id of a project
userId     | Id of a user

## Get Project Analytics

```shell
curl -X POST "https://app.seventime.se/api/2/analytics/projects" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"fromDate":"2024-01-01","toDate":"2024-12-31","groupBy":"projectType","metrics":["projectCount"]}'
```

This endpoint returns the number of projects. See [Get Time Log Analytics](#get-time-log-analytics) for the request and response format.

### HTTP Request

`POST https://app.seventime.se/api/2/analytics/projects`

Option | Values
------ | ------
dateField | `createdDate`, `startDate`, `endDate`, `completedDate`
groupBy   | `customer`, `projectType`, `department`, `resultUnit`, `status`, `invoiceStatus`, `month`, `year`
metrics   | `projectCount`

Filter | Description
------ | -----------
customerId    | Id of a customer
projectTypeId | Id of a project type
departmentId  | Id of a department
resultUnitId  | Id of a result unit
status        | Project status code
invoiceStatus | Invoice status: 0 (None), 5 (Not billable), 10 (Ready to be invoiced), 20 (Partly invoiced) or 30 (Fully invoiced)
