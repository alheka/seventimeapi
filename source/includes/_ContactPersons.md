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
      "_id": "5fb7bcd0ab7bb01d4d798762",
      "name": "Tommy",
      "title": "Utvecklare",
      "workPhone": "",
      "cellPhone": "",
      "email": "support@seventime.se",
      "customer": "5bb26376c42fb99275000080",
      "customerName": "Tommy Hellström",
      "mainContact": true,
      "isActive": true,
      "createdDate": "2020-11-17T12:06:24.281Z",
      "modifiedDate": "2020-11-17T12:06:24.281Z",
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

E.g. `https://app.seventime.se/api/2/contactPersons/?customerId=5bb26376c42fb99275000080`

Parameter | Default | Description
--------- | ------- | -----------
customerId      | | The id of the customer which the contact persons belong to. If not specified, all contact persons will be retrivied, regardless of which customer they belong to
sortBy          |  | If specified, a sort will be made on the specified parameter
sortDirection   |  | "ascending" or "descending". If specified and sortBy is specified the sort order will be ascending or descending

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
    "_id": "5fb7bcd0ab7bb01d4d798762",
    "name": "Tommy",
    "title": "Utvecklare",
    "workPhone": "",
    "cellPhone": "",
    "email": "support@seventime.se",
    "customer": "5bb2775da1640a751f000082",
    "customerName": "Tommy Hellström",
    "mainContact": true,
    "isActive": true,
    "createdDate": "2020-11-17T12:06:24.281Z",
    "modifiedDate": "2020-11-17T12:06:24.281Z",
    "systemAccount": "5112826056d961c030000001",
  },
}
```

This endpoint retrieves a contact person.

### HTTP Request

`GET https://app.seventime.se/api/2/contactPersons/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the contact person to retrieve
