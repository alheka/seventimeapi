# Work schedules

## Get Work schedules


```shell
curl "https://app.seventime.se/api/2/workSchedules" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/workSchedules";
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
        "_id": "512406df88a296a124000106",
        "name": "Heltid",
        "description": "100%",
        "isActive": true,
        "workScheduleWeeks": [
          {
            "workScheduleDays": [
              {
                "breaks": [
                  {
                    "breakStartHour": 12,
                    "breakEndHour": 13
                  }
                ],
                "numberOfWorkHours": 8,
                "startHour": 7,
                "endHour": 16
              },
              {
                "breaks": [
                  {
                    "breakStartHour": 12,
                    "breakEndHour": 13
                  }
                ],
                "numberOfWorkHours": 8,
                "startHour": 7,
                "endHour": 16
              },
              {
                "breaks": [
                  {
                    "breakStartHour": 12,
                    "breakEndHour": 13
                  }
                ],
                "numberOfWorkHours": 8,
                "startHour": 7,
                "endHour": 16
              },
              {
                "breaks": [
                  {
                    "breakStartHour": 12,
                    "breakEndHour": 13
                  }
                ],
                "numberOfWorkHours": 8,
                "startHour": 7,
                "endHour": 16
              },
              {
                "breaks": [
                  {
                    "breakStartHour": 12,
                    "breakEndHour": 13
                  }
                ],
                "numberOfWorkHours": 8,
                "startHour": 7,
                "endHour": 16
              },
              {
                "breaks": [],
                "numberOfWorkHours": 0,
                "startHour": 0,
                "endHour": 0
              },
              {
                "breaks": [],
                "numberOfWorkHours": 0,
                "startHour": 0,
                "endHour": 0
              }
            ],
            "numberOfWorkHours": 40
          }
        ]
      },
      {
        // ...
      }
  ]
}
```

This endpoint retrieves work schedules.

### HTTP Request

`GET https://app.seventime.se/api/2/workSchedules`


## Get a specific Department

```shell
curl "https://app.seventime.se/api/2/departments/59d05abdc471b72e4979135" \
  -H "Client-Secret: thisismysecretkey" \
  -H "Content-type: application/json"
```

```javascript
/* Sample with the request library */

let url = "https://app.seventime.se/api/2/workSchedules/59d05abdc471b72e4979135";
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
    "_id": "512406df88a296b124000106",
    "name": "Heltid",
    "description": "100%",
    "isActive": true,
    "workScheduleWeeks": [
      {
        "workScheduleDays": [
          {
            "breaks": [
              {
                "breakStartHour": 12,
                "breakEndHour": 13
              }
            ],
            "numberOfWorkHours": 8,
            "startHour": 7,
            "endHour": 16
          },
          {
            "breaks": [
              {
                "breakStartHour": 12,
                "breakEndHour": 13
              }
            ],
            "numberOfWorkHours": 8,
            "startHour": 7,
            "endHour": 16
          },
          {
            "breaks": [
              {
                "breakStartHour": 12,
                "breakEndHour": 13
              }
            ],
            "numberOfWorkHours": 8,
            "startHour": 7,
            "endHour": 16
          },
          {
            "breaks": [
              {
                "breakStartHour": 12,
                "breakEndHour": 13
              }
            ],
            "numberOfWorkHours": 8,
            "startHour": 7,
            "endHour": 16
          },
          {
            "breaks": [
              {
                "breakStartHour": 12,
                "breakEndHour": 13
              }
            ],
            "numberOfWorkHours": 8,
            "startHour": 7,
            "endHour": 16
          },
          {
            "breaks": [],
            "numberOfWorkHours": 0,
            "startHour": 0,
            "endHour": 0
          },
          {
            "breaks": [],
            "numberOfWorkHours": 0,
            "startHour": 0,
            "endHour": 0
          }
        ],
        "numberOfWorkHours": 40
      }
    ]
  }
}
```

This endpoint retrieves a specific department.



### HTTP Request

`GET https://app.seventime.se/api/2/workSchedules/<_id>`

### URL Parameters

Parameter | Description
--------- | -----------
_id | The _id of the work schedule to retrieve
