# Changelog

This section lists the changes in the API that can affect an integration, newest first. Changes marked **Breaking** may require changes in an integration that already uses the endpoint.

## November 2026

### Added

* [Create a Quote](#create-a-quote): create a quote or an opportunity from a quote template, with rows in the template's first price table. The rows get their prices, and the quote its totals, as when the quote is created in Seven Time.
* Paging with a cursor on the lists of contact persons, customers, departments, distributors, driver journals, expense items, expenses, invoices, machine time logs, machines, object items, price lists, projects, purchase orders, quotes, supplement orders, supplier invoices, tasks, time logs, timers, users, vehicles and work orders: the parameter `cursor` and `meta.nextCursor`, to fetch all records, or all records changed since `lastModified`, without slow deep pages. See [Paging with a cursor](#paging-with-a-cursor).
* [Get Deleted Time Logs](#get-deleted-time-logs) and [Get Deleted Expenses](#get-deleted-expenses): the ids of time logs and expenses deleted since a point in time, so that an integration can sync without fetching all records. Deletions made before the November 2026 release may be missing.
* [Get Invoices](#get-invoices), [Get Users](#get-users), [Get Work schedules](#get-work-schedules), [Get Contact Persons](#get-contact-persons), [Get Departments](#get-departments), [Get price lists](#get-price-lists), [Get Distributors](#get-distributors), [Get Machines](#get-machines), [Get Vehicles](#get-vehicles), [Get Supplement Orders](#get-supplement-orders), [Get Purchase Orders](#get-purchase-orders), [Get Machine Time Logs](#get-machine-time-logs), [Get Driver Journals](#get-driver-journals), [Get Tasks](#get-tasks), [Get Active Timers](#get-active-timers) and [Get Documents](#get-documents) (with `documentListId`): the parameter `lastModified`, to only get the records that have changed since your last call. Invoices, contact persons, departments, price lists, distributors, machines, vehicles, supplement orders, purchase orders, machine time logs, driver journals, tasks, timers and documents in the document archive also contain the fields `createdAt` and `updatedAt`. `updatedAt` is set by the server every time a record is saved.
* [Get Quotes](#get-quotes): the parameters `lastModified` and `include`, and the field `updatedAt` on quotes. Use `include` to only get the quote head and the parts you need, and `lastModified` to only get the quotes that have changed since your last call.
* [Get Supplement Orders](#get-supplement-orders): `project` is no longer required. Without it, all supplement orders of the account are listed. The `meta` property also contains `totalResourcesIsExact`, `hasMore` and `nextPage`, and `totalResources` is capped at 2000, as for the other large lists.
* User roles, user salary types, user skills, user work types and [time categories](#get-time-categories) are paged with `limit` and `page`, like the other lists. Earlier, `page` was ignored and every page returned the same results. See [Pagination](#pagination).
* All lists of types, tags and settings contain the `meta` property, except [Get Statuses](#get-statuses), which still returns an array.

### Changed

* **Breaking:** The lists of types, tags and settings that are not limited (e.g. project statuses, work order types, result units, documents, custom fields and webhook subscriptions) return all results on page 1 and an empty `data` array on page 2 and later. Earlier, every page returned all results, so a client that paged until it got no results never stopped. See [Pagination](#pagination).
* **Breaking:** Project tags, invoice tags and work order tags return `{"data": [], "meta": {...}}` when the account has no tags. Earlier, project tags and invoice tags returned an empty array, and work order tags an empty tag object.
* `sortBy` on user roles, user salary types, user skills, user work types and time categories replaces the default sort, as on the other lists. Earlier, it only decided the order between results with the same name. User roles are sorted by name by default, and can also be sorted on `userRoleId` and `userRoleName`. User skills are sorted by name by default. Earlier, they were returned in the order they were created.
* Lists sorted with `sortDirection=descending`: results with the same value in the sort field come in descending order of `_id`. Earlier, they came in ascending order of `_id`. The order between such results has never been guaranteed, and paging is still stable: every result is on exactly one page.
* [Create a Time Log](#create-a-time-log) and [Update a Time Log](#update-a-time-log): a time log that is not invoiceable keeps its `pricePerHour` (the one sent, or the stored one). `price` and the prices of its custom fields are 0. Earlier, `pricePerHour` was set to 0. The price is then right if the time log is made invoiceable again.
* [Get Time Log Analytics](#get-time-log-analytics): `revenue` only counts invoiceable time logs. Earlier, the price of a time log that was not invoiceable could be counted.
* Machine time on time logs and machine time logs with a billing model (debit schedule): `pricePerHour` matches `price`. With a schedule or a machine price list it is the price per hour the normal time is charged with (including the operator). With a minimum charge or manual registration it is `price` divided by the invoiceable time (0 when the invoiceable time is 0). `price` is unchanged. [Update a Machine Time Log](#update-a-machine-time-log) with manual registration also saves `time` and `invoiceableTime` as computed from the rows.
* A missing `Client-Secret` header returns HTTP 401 instead of HTTP 500. See [Header fields](#header-fields).
* Requests with an OAuth access token: to change a document or folder that another user created in the Documents module, the user needs the permission "Edit others documents/folders". To delete a document or folder, the user needs "Create/edit documents/folders" and "Remove documents/folders", plus "Remove others documents/folders" if another user created it. This is the same as in Seven Time. Documents on projects, work orders and other records follow the rules of the record. API keys are not affected.

### Fixed

* Time logs and expenses that are created in Seven Time by copying or distributing existing rows (e.g. copying the previous day) get the time they were created as `updatedAt`. Earlier, they could keep the `updatedAt` of the original row, and were then missing when [time logs](#get-time-logs) or [expenses](#get-expenses) were fetched with `lastModified`.
* Articles (expense items) that are copied in Seven Time get the time they were copied as `updatedAt`. Earlier, a copy kept the `updatedAt` of the original article, and was then missing when [expense items](#get-expenses-items) were fetched with `lastModified`.
* [Create a Time Log](#create-a-time-log) and [Update a Time Log](#update-a-time-log): when `time` is computed from `timestamp` and `endTimestamp`, milliseconds in the timestamps are ignored. Earlier, e.g. 08:00:00.999–12:00:00.000 could give one minute less.
* [Update an Invoice](#update-an-invoice) and [Update a Supplier Invoice](#update-a-supplier-invoice): `createdAt` and `updatedAt` in the request are ignored, and `updatedAt` is set by the server. Earlier, `createdAt` set to `null` or an empty string returned HTTP 500.

## October 2026

Released on 30 October 2026.

### Added

* [Object Items](#object-items): endpoints to list, get, create and update object items, [Get Object Item Documents](#get-object-item-documents), [webhook events](#available-events) for object items and their documents, and Zapier triggers for object items.
* [Create an Invoice](#create-an-invoice) and [Update an Invoice](#update-an-invoice): the delivery date `actualDeliveryDate`. If it is not specified on a new invoice for a work order, it can be set from the date the work order was completed (an invoice setting in Seven Time).
* [Update an Invoice](#update-an-invoice): version control with `__v`. If the invoice has been modified since it was fetched, the update is rejected with HTTP 409.
* [Create a Customer](#create-a-customer): `expenseDiscountWholeSale`, `expenseWholeSaleProfitMargin` and `expenseUseArticleNumberProfitMargin`, for discounts and markups on wholesale articles, including markup on purchase price per article number.
* [Get supplier invoices](#get-supplier-invoices): the parameter `includeDistributed`. Together with `project`, it also includes supplier invoices that are distributed on several projects with a row on the project.

### Changed

* **Breaking:** [Create an Invoice](#create-an-invoice) and [Update an Invoice](#update-an-invoice) return HTTP 400 instead of HTTP 500 for validation errors, e.g. an id that is not found or an invalid value. HTTP 500 is only returned for server errors.
* **Breaking:** Time logs and machine time logs that are attested (`status` 3) cannot be updated or deleted, and `status` can only be changed between 1 (new) and 2 (finished). On time logs, `isAbsence` cannot be changed, and `attestedBy` and `attestItem` are ignored. See [Update a Time Log](#update-a-time-log) and [Update a Machine Time Log](#update-a-machine-time-log).
* **Breaking:** Webhook subscriptions: a new `targetUrl` must start with `https://` and must not point to localhost or a private network address. A company can have at most 100 active subscriptions. Redirects are not followed, and no requests are sent while the API key that created the subscription is deactivated or deleted. Subscriptions created before October 2026 may still use `http://`. See [Webhook requests](#webhook-requests) and [Create a Webhook Subscription](#create-a-webhook-subscription).
* [Create a User](#create-a-user): a `userRoleId` that is not one of the ids from [Get User Roles](#get-user-roles) returns HTTP 400.
* [Get Statuses](#get-statuses): `entityType` must be 200, 300, 500, 4200 or 4400. Another value returns HTTP 400.
* A `limit` that is not a number gives the default limit (100). Earlier, all results were returned. See [Pagination](#pagination).
* Requests with an OAuth access token (e.g. through the Seven Time MCP server) follow the connected user's permissions as in Seven Time, also for other users' time logs, absence, timers, tasks and documents. A user without the permission to see financial information doesn't get prices, costs or amounts. API keys are not affected. See [Authentication](#authentication).
* [Create a Time Log](#create-a-time-log): if `customer` is not specified, the time log gets the customer of the project when Seven Time is set to have a dependency between customer and project.

### Fixed

* [Create a Time Log](#create-a-time-log) and [Update a Time Log](#update-a-time-log): `price` is calculated from the price per hour and the time (or the invoiceable time). Earlier, `price` could be wrong when `pricePerHour` was specified. A specified `pricePerHour` is used as it is, also 0, and a value that is not a number returns HTTP 400. A time log that is not invoiceable gets the invoiceable time 0 and the price 0.
* Supplier invoices: the `path` of a document is a download URL that is valid for one hour. Earlier, it was an internal path that returned HTTP 403. The internal path is in `realPath`.
