# Tasks
## Get Tasks


```shell
curl "https://app.seventime.se/api/2/tasks/?limit=3&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/tasks/?limit=3&page=1";
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
    "totalResources": 280, 
    "totalPages": 94, 
    "currentPage": 1 },
  "data": [
    {
      "_id": "5dd0i31j238019132k328321k",
      "title": "API task",
      "tags": [],
      "dependsOn": [],
      "dependents": [],
      "reminders": [],
      "createDate": "2019-11-22T14:51:42.224Z",
      "createdByUser": "5112891383213mk0002",
      "__v": 0,
      "taskStatusRef": "5e8d2137213h312a2034d",
      "rank": "0|i000yv:"
    },
    {
      // ...
    }
  ]
}

```

This endpoint retrieves tasks.

### HTTP Request

`GET https://app.seventime.se/api/2/tasks`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
title              |  | If specified, tasks that match the parameter will be included.
fromStartDate      |  | If specified, tasks that start after this date will be included. The date has to be in the format 'YYYY-MM-HH HH:MM'.
toStartDate        |  | If specified, tasks that start before this date will be included. The date has to be in the format 'YYYY-MM-HH HH:MM'.
fromDueDate        |  | If specified, tasks that are due after this date will be included. The date has to be in the format 'YYYY-MM-HH HH:MM'. 
toDueDate          |  | If specified, tasks that are due before this date will be included. The date has to be in the format 'YYYY-MM-HH HH:MM'.
user               |  | If specified, tasks that match the parameter will be included.
project            |  | If specified, tasks that match the parameter will be included.
customer           |  | If specified, tasks that match the parameter will be included.
quote              |  | If specified, tasks that match the parameter will be included.
workOrder          |  | If specified, tasks that match the parameter will be included.
invoice            |  | If specified, tasks that match the parameter will be included.
machine            |  | If specified, tasks that match the parameter will be included.
objectItem         |  | If specified, tasks that match the parameter will be included.
sortBy             |  | If specified, a sort will be made on the specified parameter
sortDirection      |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending





## Get a specific Task

```shell
curl "https://app.seventime.se/api/2/tasks/5dd0i31j238019132k328321k" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/tasks/5dd0i31j238019132k328321k";
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
    "_id": "5dd0i31j238019132k328321k",
    "title": "API task",
    "tags": [],
    "dependsOn": [],
    "dependents": [],
    "reminders": [],
    "createDate": "2019-11-22T14:51:42.224Z",
    "createdByUser": "5112891383213mk0002",
    "__v": 0,
    "taskStatusRef": "5e8d2137213h312a2034d",
    "rank": "0|i000yv:"
  }
}
```

This endpoint retrieves a specific task.



### HTTP Request

`GET https://app.seventime.se/api/2/tasks/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the task to retrieve

## Create a task

```shell
curl -X POST "https://app.seventime.se/api/2/tasks/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"createdByUser":"5f48eb3e65d7ee4926574851","title":"API task"}'
```

```javascript
let jsonData = {
  createdByUser: '5f48eb3e65d7ee4926574851',
  title: 'API task'
};

let options = {
  url: 'https://app.seventime.se/api/2/tasks',
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
    console.error("ERROR! Unable to create task: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "tags": [],
  "dependsOn": [],
  "dependents": [],
  "_id": "6705973h3j1733m33j3382",
  "reminders": [],
  "todoItems": [],
  "documents": [],
  "notes": [],
  "createDate": "2024-10-08T11:01:36.674Z",
  "title": "API uppgift",
  "taskStatusRef": "5e8dea9332u23123ff34d",
  "rank": "0|i001pf:",
  "createdByUser": "5f48eb3e65d7ee4926574851",
  "project": null,
  "projectName": null,
  "workOrder": null,
  "workOrderTitle": null,
  "workOrderNumber": null,
}
```

This endpoint creates a task

### HTTP Request

`POST https://app.seventime.se/api/2/tasks/`

### POST Parameters

Parameter | Type    | Required? | Description
--------- |---------|-----------| -----------
createdByUser       | String  | Yes       | Id of the user who created the task
title               | String  | Yes       | Title of the task
startDate           | String  | No        | Starting date for the task. This must be in the format 'YYYY-MM-DD'
dueDate             | String  | No        | Due date for the tasks. This must be in the format 'YYYY-MM-DD'
workOrder           | String  | No        | Id of the work order that the task will belong to
user                | String  | No        | Id of the user that will be assigned to the task
project             | String  | No        | Id of the project
customer            | String  | No        | Id of the customer
quote               | String  | No        | Id of the quote
invoice             | String  | No        | Id of the invoice
machine             | String  | No        | Id of the machine
completed            | Boolean | No        | Set if the task is completed or not

## Update a Task

```shell
curl -X PUT "https://app.seventime.se/api/2/tasks/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"6705973h3j1733m33j3382","modifiedByUser":"5f48eb3e65d7ee4926574851","title":"Updated API task"}'
```

```javascript
let jsonData = {
  _id: '6705973h3j1733m33j3382',
  modifiedByUser: '5f48eb3e65d7ee4926574851',
  title: 'Updated API task'
};

let options = {
  url: 'https://app.seventime.se/api/2/tasks',
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
    console.log("Task updated: _id: " + body._id);
  } else {
    console.error("ERROR! Unable to update task: " + error);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "tags": [],
  "dependsOn": [],
  "dependents": [],
  "_id": "6705973h3j1733m33j3382",
  "reminders": [],
  "todoItems": [],
  "documents": [],
  "notes": [],
  "createDate": "2024-10-08T11:01:36.674Z",
  "title": "Updated API task",
  "taskStatusRef": "5e8dea9332u23123ff34d",
  "rank": "0|i001pf:",
  "createdByUser": "5f48eb3e65d7ee4926574851",
  "project": null,
  "projectName": null,
  "workOrder": null,
  "workOrderTitle": null,
  "workOrderNumber": null,
}
Task updated: _id: 6705973h3j1733m33j3382"
```

This endpoint updates a task

### HTTP Request

`PUT https://app.seventime.se/api/2/tasks/`

### PUT Parameters
The table below shows the required fields. Other available fields can be found in the section 'Create a Task'.

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id             | String | Yes | Id of the task
modifiedByUser  | String | Yes | Id of the user who made the change

## Delete a Task

```shell
curl -X DELETE "https://app.seventime.se/api/2/tasks/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"6705973h3j1733m33j3382","deletedByUser":"5f48eb3e65d7ee4926574851"}'
```

```javascript
let jsonData = {
  _id: '51203146506d961c35798485',
  deletedByUser: '51203146506d961c03036589741'
};

let options = {
  url: 'https://app.seventime.se/api/2/tasks',
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
    console.log("Task deleted: _id: " + body._id);
  } else {
    console.error("ERROR! Unable to delete task: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{ 
  "_id": "5f48eb3e65d7ee4926574851"
}
"Task deleted: _id: 5f48eb3e65d7ee4926574851"
```

This endpoint deletes a task

### HTTP Request

`DELETE https://app.seventime.se/api/2/tasks/`

### DELETE Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id             | String | Yes | Id of the task
