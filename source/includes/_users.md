# Users
## Get Users

```shell
curl "https://app.seventime.se/api/2/users/?limit=10&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/users/?&limit=100&page=1";
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
    "totalResources": 4712,
    "totalPages": 48,
    "currentPage": 3
  },
  "data": [
    {
      "_id": "5f48eb3e65d7ee4942c4602",
      "firstName": "Tommy",
      "lastName": "Hellström",
      "email": "tommy@nummer7.se",
      "personalNumber": "",
      "employeeNumber": "",
      "userName": "20200828",
      "workPhone": "",
      "cellPhone": "",
      "createdDate": "2020-08-28T11:32:14.452Z",
      "modifiedDate": "2020-08-28T11:33:36.675Z",
      "userRoleId": 10,
      "isActive": true,
      "isActivated": true,
      "language": "SV"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves users, a maximum of 500 users will be returned.

### HTTP Request

`GET https://app.seventime.se/api/2/users`

### Query Parameters

E.g. `https://app.seventime.se/api/2/users/?name=Tommy Hellström`

Parameter | Default | Description
--------- | ------- | -----------
name              |  | If specified, users that match the parameter will be included.
personNumber      |  | If specified, users that match the parameter will be included.
department        |  | If specified, users that match the parameter will be included.
userRole          |  | If specified, users that match the parameter will be included.
isActive          |  | If specified, users that match the parameter will be included. This must be a boolean
isActivated       |  | If specified, users that match the parameter will be included. This must be a boolean
defaultSalaryType |  | If specified, users that match the parameter will be included.
userSkills        |  | If specified, users that match the parameter will be included.
sortBy            |  | If specified, a sort will be made on the specified parameter
sortDirection     |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending


## Get a specific User

```shell
curl "https://app.seventime.se/api/2/users/59312765ad961c0318eb0a2" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/users/59312765ad961c0318eb0a2";
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
  "data":
  {
    "_id": "59312765ad961c0318eb0a2",
    "firstName": "Tommy",
    "lastName": "Hellström",
    "email": "tommy@nummer7.se",
    "personalNumber": "",
    "employeeNumber": "2",
    "userName": "tommy",
    "workPhone": "0431-360050",
    "cellPhone": "070-4580425",
    "createdDate": "2013-02-06T16:18:40.588Z",
    "modifiedDate": "2020-11-16T10:39:01.762Z",
    "userRoleId": 30,
    "isActive": true,
    "isActivated": true,
    "language": "EN"
  }
}
```

This endpoint retrieves a specific user



### HTTP Request

`GET https://app.seventime.se/api/2/users/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the user to retrieve

## Get User Roles

```shell
curl "https://app.seventime.se/api/2/userRoles/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/userRoles/";
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
      "userRoleId": 1,
      "userRoleName": "Administratör"
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves user roles, a maximum of 500 user roles will be returned.



### HTTP Request

`GET https://app.seventime.se/api/2/userRoles/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get User Salary types

```shell
curl "https://app.seventime.se/api/2/defaultSalaryTypes/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/defaultSalaryTypes/";
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
      "_id": "5834419c7a27db6932000052",
      "name": "Övertid",
      "description": "",
      "code": "123",
      "isAbsenceTimeType": false,
      "isRuleType": false,
      "absenceTimeCategory": null,
      "absenceTimeCategoryName": "",
      "unitType": "1",
      "canBeRegistered": true,
      "salaryAmount": 0,
      "typeInSalarySystem": 10
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves user salary types, a maximum of 500 salary types will be returned.



### HTTP Request

`GET https://app.seventime.se/api/2/defaultSalaryTypes/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get User Skills

```shell
curl "https://app.seventime.se/api/2/userSkills/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/userSkills/";
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
      "_id": "59f9d1c53ffd5f932a000067",
      "skillTitle": "Höga arbeten",
      "requireEducations": [
        "5a54ea1f7a7fe3c26200006e"
      ]
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves user skills, a maximum of 500 user skills will be returned.

### HTTP Request

`GET https://app.seventime.se/api/2/userSkills/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get User Work Types

```shell
curl "https://app.seventime.se/api/2/userWorkTypes/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/userWorkTypes/";
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
      "_id": "5f442181e62efdb4a3a7d9c6d",
      "name": "Programmerare",
      "pricePerHour": 555,
    },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves user roles, a maximum of 500 user roles will be returned.


### HTTP Request

`GET https://app.seventime.se/api/2/userRoles/`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
sortBy |  | If specified, a sort will be made on the specified parameter
sortDirection |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Create a User

```shell
  curl -X POST "https://app.seventime.se/api/2/users/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"createdByUser":"5f48eb3e65d7ee4942c46eeb","firstName":"Tommy","lastName":"Hellström","email":"tommy@nummer7.se","userName":"TommyH","userRolesId":1"}'
```

```javascript
let jsonData = {
  createdByUser: '5f48eb3e65d7ee4942c46eeb',
  firstName: 'Tommy',
  lastName: 'Hellström',
  email: 'tommy@nummer7.se',
  userName: 'TommyH',
  userRoleId: 1,
};

let options = {
  url: 'https://app.seventime.se/api/2/users',
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
    console.error("ERROR! Unable to create user: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "_id": "5fb3e157f795553d05751946",
  "firstName": "Tommy",
  "lastName": "Hellström",
  "email": "tommy@nummer7.se",
  "personalNumber": "",
  "employeeNumber": "",
  "userName": "TommyH",
  "workPhone": "",
  "cellPhone": "",
  "createdDate": "2020-11-17T14:42:31.533Z",
  "modifiedDate": "2020-11-17T14:42:31.533Z",
  "userRoleId": 1,
  "isActive": false,
  "isActivated": false,
  "language": "SV"
}
```

This endpoint creates a user.

### HTTP Request

`POST https://app.seventime.se/api/2/users/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
firstName          | String   | Yes | First name of the user
lastName           | String   | Yes | Last name of the user
email              | String   | Yes | Email of the user
userName           | String   | Yes | Username
userRoleId         | String   | Yes | User role id
employeeNumber     | String   | No  | EmployeeNumber
workPhone          | String   | No  | Work phone number
cellPhone          | String   | No  | Cell phone number
isActive           | Boolean  | No  | Should the user be active?
isActivated        | Boolean  | No  | Should the user be activated?
password           | String   | No  | Password of the user
language           | String   | No  | Language of the user as a language code (e.g SV for Swedish). If not specified, this will we set to SV.

## Update a User

```shell
  curl -X PUT "https://app.seventime.se/api/2/users/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fb3e157f795553d05751946","modifiedByUser":"5f48eb3e65d7ee4942c46eeb","firstName":"Tommy","lastName":"Hellström","userName":"TommyH"}' 
```

```javascript
let jsonData = {
  _id: '5fb3e157f795553d05751946',
  modifiedByUser: '5f48eb3e65d7ee4942c46eeb',
  firstName: 'Tommy',
  lastName: 'Hellström',
  userName: 'TommyH'
};

let options = {
  url: 'https://app.seventime.se/api/2/users',
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
    console.log("User updated: " + body.firstName + ", _id: " + body._id);
  } else {
    console.error("ERROR! Unable to update user: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "_id": "5fb3e157f795553d05751946",
  "firstName": "Tommy",
  "lastName": "Hellström",
  "email": "tommy@nummer7.se",
  "userName": "TommyH",
  "createdDate": "2020-11-17T14:42:31.533Z",
  "modifiedDate": "2020-12-11T13:25:07.332Z",
  "userRoleId": 1,
  "isActive": true,
  "isActivated": false,
  "language": "SV"
}
"User updated: Tommy, _id: 5fb3e157f795553d05751946"
```

This endpoint updates a specific user.

### HTTP Request

`PUT https://app.seventime.se/api/2/users/`

### PUT Parameters

The table below shows the required fields. Other available fields can be found in the section 'Create a User'.

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                | String   | Yes | Id of the user
modifiedByUser     | String   | Yes | Id of the user who made the change

<!---
## Delete a User

```shell
  curl -X DELETE "https://app.seventime.se/api/2/users/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"5fb3e157f795553d05751946","deletedByUser":"5f48eb3e65d7ee4942c46eeb"}' 
```

```javascript
let jsonData = {
  _id: '5fb3e157f795553d05751946',
  deletedByUser: '5f48eb3e65d7ee4942c46eeb'
};

let options = {
  url: 'https://app.seventime.se/api/2/users',
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
    console.log("User deleted: " + body.firstName + ", _id: " + body._id);
  } else {
    console.error("ERROR! Unable to delete user: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "_id": "5fb3e157f795553d05751946",
  "firstName": "Tommy",
  "lastName": "Hellström",
}
"User deleted: Tommy, _id: 5fb3e157f795553d05751946"
```

This endpoint deletes a specific user.

### HTTP Request

`DELETE https://app.seventime.se/api/2/users/`

### DELETE Parameters


Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                | String   | Yes | Id of the user
deletedByUser      | String   | Yes | Id of the user who made the delete
-->
