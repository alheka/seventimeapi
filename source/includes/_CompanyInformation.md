# Company Information

## Get Company Information

```shell
curl "https://app.seventime.se/api/2/companyInformation/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/companyInformation/";
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
    "id": "5171464ffbb708f33e000001",
    "companyName": "Company AB",
    "address": "Street 1",
    "zipCode": "111 22",
    "city": "Stockholm",
    "organizationNumber": "556677-8899"
  }
}
```

This endpoint retrieves information about the company connected to the API key.

### HTTP Request

`GET https://app.seventime.se/api/2/companyInformation/`

### URL Parameters

No parameters

If no company information is found for the account, HTTP 500 is returned with the `errorMessage` "Could not find company information".
