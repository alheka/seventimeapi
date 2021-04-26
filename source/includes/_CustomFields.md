# Custom Fields
## Get Custom fields

```shell
curl "https://app.seventime.se/api/2/customFields/?entityType=200" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/customFields/?entityType=200";
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
    { "_id": "572cc7advab059714hcfca51",
      "selectFieldData": [],
      "fieldType": 100,
      "fieldName": "Kund",
      "include": true,
      "required": false },
    {
      // ...
    }
  ]
}
```

This endpoint retrieves custom fields.

### HTTP Request

`GET https://app.seventime.se/api/2/customFields/?entityType=<entityType>`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
entityType                          | 100 | Number corresponding to entity type. See table below for available types.

**Entity types**

Code | Description
--------- | ----------- 
100   | Time log
200   | Work order
300   | Tasks
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
