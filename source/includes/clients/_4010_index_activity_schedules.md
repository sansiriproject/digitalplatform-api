## activity_schedules#index

```javascript
const request = require("request-promise");
const jwt = require("jsonwebtoken");

let apiKey = "apiKey";
let apiSecret = "apiSecret";
let activityUid = "sirnbiusASDIIH";

const hostname = "https://digitalplatform-api.dev.sansiriproject.com";
const apiPath = `/api/v1/client/${apiKey}/activities/${activityUid}/activity_schedules;

let expTime = Math.floor(Date.now() / 1000) + 60; // expiration + 60 seconds
let token = jwt.sign({ api_key: apiKey, exp: expTime }, apiSecret);

let options = {
  uri: `${hostname}${apiPath}`,
  headers: {
    CMSAuthToken: `Bearer ${token}`
  },
  json: true
};
request(options)
  .then(function(response) {
    console.log("RESPONSE", response);
  })
  .catch(function(err) {
    console.log("ERR", err);
  });
```

> The above command returns JSON structured like this:

```json
[
    {
        "uid": "7PZBMHU16zx5",
        "id": 2,
        "start_datetime": "2019-09-19T12:09:05.000+07:00",
        "end_datetime": "2019-09-20T12:08:43.000+07:00",
        "description": "description",
        "created_at": "2019-09-19T12:09:11.736+07:00",
        "updated_at": "2019-09-19T12:10:56.524+07:00",
        "created_by": null,
        "updated_by": null,
        "maximum_seats_per_user": 2
    }
]
```

This endpoint retrieves one activity from uid.

### HTTP Request

`GET /api/v1/client/${apiKey}/activities/${activityUid}/activity_schedules`

<aside class="notice">
Remember — a happy api require `activityUid`.
</aside>

### Response

`TYPE: Object`

| Parameter          | example      | Description                       |
| ------------------ | ------------ | --------------------------------- |
| uid                | "asdfuirtXX" | URL Safe Base64 String            |   
| start_datetime | "2019-09-19T12:09:05.000+07:00"  | Schedule start date/time |
| end_datetime | "2019-09-20T12:08:43.000+07:00"  | Schedule end date/time |
| description        |  "description" |                   |
| maximum_seats_per_user          | 2 |                   |
