# Webhook Subscriptions

Webhook subscriptions let you receive a HTTP `POST` request to your own URL when something happens in Seven Time, e.g. when a work order is created or an invoice is updated. One subscription is created per event.

### Available events

Event | Description
--------- | -----------
workorder.created | A work order was created
workorder.updated | A work order was updated
project.created   | A project was created
project.updated   | A project was updated
customer.created  | A customer was created
customer.updated  | A customer was updated
invoice.created   | An invoice was created
invoice.updated   | An invoice was updated
invoice.sent      | An invoice was sent
quote.created     | A quote was created
quote.updated     | A quote was updated
quote.sent        | A quote was sent
quote.opened      | A quote was opened by the recipient
quote.approved    | A quote was approved
quote.rejected    | A quote was rejected
timelog.created   | A time log was created
timelog.updated   | A time log was updated
task.created      | A task was created
task.updated      | A task was updated

### Webhook requests

> A webhook request sent to your URL looks like this:

```json
{
  "event": "workorder.created",
  "timestamp": "2024-01-15T08:00:00.000Z",
  "data": {
    "_id": "5bae34dca878b5497748",
    "title": "Service",
    "workOrderNumber": 1234
    // ...
  }
}
```

> Verifying the signature in Node.js:

```javascript
const crypto = require('crypto');

// rawBody is the raw request body as a string
const expectedSignature = crypto
  .createHmac('sha256', secret)
  .update(rawBody)
  .digest('hex');

const isValid = crypto.timingSafeEqual(
  Buffer.from(expectedSignature),
  Buffer.from(req.headers['x-seventime-signature'])
);
```

When an event occurs, Seven Time sends a `POST` request with a JSON body to the `targetUrl` of every active subscription for that event. The body contains:

Field | Description
--------- | -----------
event     | The event that occurred, e.g. `workorder.created`
timestamp | Date and time when the request was sent, in ISO 8601 format
data      | The object the event concerns. It has the same structure as when fetching the object from the corresponding endpoint, e.g. a work order for `workorder.*` events

Each request includes the header `X-SevenTime-Signature`. It is a hex encoded HMAC-SHA256 of the request body, signed with the `secret` of the subscription. Use it to verify that the request was sent by Seven Time.

Your endpoint should respond with a 2xx status code within 10 seconds. If the request fails, it is retried up to two more times: after 1 minute and after 5 more minutes. If your endpoint responds with `410 Gone`, the subscription is deactivated and no further requests are sent.

## Get Webhook Subscriptions

```shell
curl "https://app.seventime.se/api/2/webhookSubscriptions/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/webhookSubscriptions/";
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
      "_id": "65a50f80d1e44854f9c54321",
      "targetUrl": "https://example.com/seventime/webhook",
      "eventType": "workorder.created",
      "isActive": true,
      "createdAt": "2024-01-15T08:00:00.000Z"
    },
    {
      "_id": "65a50f80d1e44854f9c54322",
      "targetUrl": "https://example.com/seventime/old-webhook",
      "eventType": "invoice.sent",
      "isActive": false,
      "deactivatedAt": "2024-02-01T10:00:00.000Z",
      "deactivatedReason": "Webhook delivery received HTTP 410 Gone from https://example.com/seventime/old-webhook",
      "createdAt": "2024-01-15T08:00:00.000Z"
    }
  ]
}
```

This endpoint retrieves all webhook subscriptions. The `secret` of a subscription is not included.

### HTTP Request

`GET https://app.seventime.se/api/2/webhookSubscriptions/`

## Get a specific Webhook Subscription

```shell
curl "https://app.seventime.se/api/2/webhookSubscriptions/65a50f80d1e44854f9c54321" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/webhookSubscriptions/65a50f80d1e44854f9c54321";
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
    "_id": "65a50f80d1e44854f9c54321",
    "targetUrl": "https://example.com/seventime/webhook",
    "eventType": "workorder.created",
    "isActive": true,
    "createdAt": "2024-01-15T08:00:00.000Z"
  }
}
```

This endpoint retrieves a specific webhook subscription. The `secret` of the subscription is not included.

### HTTP Request

`GET https://app.seventime.se/api/2/webhookSubscriptions/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the webhook subscription to retrieve

## Create a Webhook Subscription

```shell
curl -X POST "https://app.seventime.se/api/2/webhookSubscriptions/" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json" \
  -d '{"targetUrl":"https://example.com/seventime/webhook","event":"workorder.created"}'
```

```javascript
let jsonData = {
  targetUrl: 'https://example.com/seventime/webhook',
  event: 'workorder.created'
};

let options = {
  url: 'https://app.seventime.se/api/2/webhookSubscriptions',
  json: jsonData,
  headers: {
    "Client-Secret": "thisismysecretkey",
    "Content-Type": "application/json",
    "Accept": 'application/json'
  }
};

request.post(options, function (error, response, body) {
  if (!error && response.statusCode === 201) {
    console.log(body);
  } else {
    console.error("ERROR! Unable to create webhook subscription: " + error);
    console.error(body);
  }
});
```

> The above command returns HTTP status 201 and JSON structured like this:

```json
{
  "id": "65a50f80d1e44854f9c54321",
  "targetUrl": "https://example.com/seventime/webhook",
  "event": "workorder.created",
  "secret": "9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08",
  "createdAt": "2024-01-15T08:00:00.000Z"
}
```

This endpoint creates a webhook subscription. The subscription is active directly.

The response contains the `secret` used to sign the webhook requests. The secret is only returned when the subscription is created, so store it in a safe place.

### HTTP Request

`POST https://app.seventime.se/api/2/webhookSubscriptions/`

### POST Parameters

Parameter | Type | Required? | Description
--------- | ----------- | ----------- | -----------
targetUrl | String | Yes | URL that will receive webhook requests. Must start with `http://` or `https://`
event     | String | Yes | Event to subscribe to. See [available events](#available-events)

## Delete a Webhook Subscription

```shell
curl -X DELETE "https://app.seventime.se/api/2/webhookSubscriptions/65a50f80d1e44854f9c54321" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-Type: application/json"
```

```javascript
let options = {
  url: 'https://app.seventime.se/api/2/webhookSubscriptions/65a50f80d1e44854f9c54321',
  headers: {
    "Client-Secret": "thisismysecretkey",
    "Content-Type": "application/json",
    "Accept": 'application/json'
  }
};

request.delete(options, function (error, response, body) {
  if (!error && response.statusCode === 200) {
    console.log(body);
  } else {
    console.error("ERROR! Unable to delete webhook subscription: " + error);
    console.error(body);
  }
});
```

> The above command returns JSON structured like this:

```json
{
  "result": true
}
```

This endpoint deletes a webhook subscription.

### HTTP Request

`DELETE https://app.seventime.se/api/2/webhookSubscriptions/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the webhook subscription to delete
