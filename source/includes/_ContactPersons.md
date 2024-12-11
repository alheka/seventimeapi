# Contact Persons

## Get Contact Persons


```shell
curl "https://app.seventime.se/api/2/contactPersons/?limit=2&page=1" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/contactPersons/?limit=5&page=1";
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
    "totalResources": 3,
    "totalPages": 1,
    "currentPage": 1
  },
  "data": [
    {
      "_id": "5fb7bcd0ab7bb01d4d54832",
      "name": "Anna",
      "title": "Utvecklare",
      "workPhone": "",
      "cellPhone": "",
      "email": "email@company.com",
      "customer": "5bb26376c4nj551167",
      "customerName": "Anna Andersson",
      "mainContact": true,
      "isActive": true,
      "createdDate": "2020-11-17T12:06:24.281Z",
      "modifiedDate": "2020-11-17T12:06:24.281Z"
    },
    {
      // ...
    }
  ]
}

```

This endpoint retrieves contact persons.

### HTTP Request

`GET https://app.seventime.se/api/2/contactPersons`

### Query Parameters

E.g. `https://app.seventime.se/api/2/contactPersons/?customerId=5bb26376c4nj551167`

Parameter | Default | Description
--------- |---------| -----------
customerId      |         | The id of the customer which the contact persons belong to. If not specified, all contact persons will be retrivied, regardless of which customer they belong to
name            |         | The name of the contact persons
sortBy          |         | If specified, a sort will be made on the specified parameter
sortDirection   |         | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

## Get a specific Contact Person

```shell
curl "https://app.seventime.se/api/2/contactPersons/5fb7bcd0ab7bb01d4d798762" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/contactPersons/5fb7bcd0ab7bb01d4d798762";
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
    "_id": "5fb7bcd0ab7bb01d4d54832",
    "name": "Anna",
    "title": "Utvecklare",
    "workPhone": "",
    "cellPhone": "",
    "email": "email@company.com",
    "customer": "5bb26376c4nj551167",
    "customerName": "Anna Andersson",
    "mainContact": true,
    "isActive": true,
    "createdDate": "2020-11-17T12:06:24.281Z",
    "modifiedDate": "2020-11-17T12:06:24.281Z",
  }
}
```

This endpoint retrieves a contact person.

### HTTP Request

`GET https://app.seventime.se/api/2/contactPersons/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the contact person to retrieve

## Create a Contact Person
```shell
Curl -X POST "https://app.seventime.se/api/2/contactPersons/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"customer":"5f48eb712ebe7ebe6eb37b","name":"Anna Andersson","title":"Chef","workPhone":"","cellPhone":"","email":"email@company.com","isActive":"true","mainContact":"false"}'
```

```javascript
let jsonData = {
  customer: '5f48eb712ebe7ebe6eb37b',
  name: 'Anna Andersson',
  title: 'Utvecklare',
  workPhone: '',
  cellPhone: '',
  email: 'email@company.com',
  isActive: true,
  mainContact: false
};

let options = {
  url: 'https://app.seventime.se/api/2/contactPersons',
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
    console.error("ERROR! Unable to create contact person: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "_id": "5fb7bcd0ab7bb01d4d54832",
  "name": "Anna",
  "title": "Utvecklare",
  "workPhone": "",
  "cellPhone": "",
  "email": "email@company.com",
  "customer": "5bb26376c4nj551167",
  "customerName": "Anna Andersson",
  "mainContact": true,
  "isActive": true,
  "createdDate": "2020-11-17T12:06:24.281Z",
  "modifiedDate": "2020-11-17T12:06:24.281Z",
}
```

This endpoint creates a contact person.

### HTTP Request

`POST https://app.seventime.se/api/2/contactPersons/`

### POST Parameters

Parameter | Type    | Required? | Description
--------- |---------| ----------- | -----------
customer            | String  | Yes | Id of the customer that the contact person will belong to
name                | String  | Yes | Name of the contact person
title               | String  | No | Title
workPhone           | String  | No | Work phone
cellPhone           | String  | No | Cell phone
email               | String  | No | Email
isActive            | Boolean | No | Is the contact person active?
mainContact         | Boolean | No | Main contact

## Update a Contact person

```shell
curl -X PUT "https://app.seventime.se/api/2/contactPersons/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"_id":"571f61330c7f498a4712448b","isActive":"false"}' 
```

```javascript
let jsonData = {
  _id: '571f61330c7f498a4712448b',
  isActive: false
};

let options = {
  url: 'https://app.seventime.se/api/2/contactPersons',
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
    console.log("Contact person updated: " + body.name + ", _id: " + body._id);

  } else {
    console.error("ERROR! Unable to update contact person: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json 
{
  "_id": "5fb7bcd0ab7bb01d4d54832",
  "name": "Anna",
  "title": "Utvecklare",
  "workPhone": "",
  "cellPhone": "",
  "email": "email@company.com",
  "customer": "5bb26376c4nj551167",
  "customerName": "Anna Andersson",
  "mainContact": true,
  "isActive": true,
  "createdDate": "2020-11-17T12:06:24.281Z",
  "modifiedDate": "2020-11-17T12:06:24.281Z",
}
"Contact person updated: Anna, _id: 5fb7bcd0ab7bb01d4d54832"
```

This endpoint updates a contact person.

### HTTP Request

`PUT https://app.seventime.se/api/2/contactPersons/`

### PUT Parameters
The table below shows the required fields. Other available fields can be found in the section 'Create a Contact Person'.


Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
_id                 | String | Yes | Id of the contact person
