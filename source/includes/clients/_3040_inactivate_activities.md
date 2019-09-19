## activities/activities#inactivate

```javascript
const request = require("request-promise");
const jwt = require("jsonwebtoken");

let apiKey = "apiKey";
let apiSecret = "apiSecret";
let activityUid = "sirnbiusASDIIH";

const hostname = "https://digitalplatform-api.dev.sansiriproject.com";
const apiPath = `/api/v1/client/${apiKey}/activities/${activityUid}/inactivate`;

let expTime = Math.floor(Date.now() / 1000) + 60; // expiration + 60 seconds
let token = jwt.sign({ api_key: apiKey, exp: expTime }, apiSecret);

let options = {
  method: "PATCH",
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
{
    "locale": "en",
    "client_uid": "171s_vNNF9yI",
    "uid": "NB2sMQWstgQZ",
    "id": 50,
    "name": "test client activity Hello",
    "description": "description",
    "shop_name": "Shop1",
    "condition_detail": "condition",
    "location": "location",
    "status": "inactive",
    "running_number": "AT190027",
    "activity_conditions": [
        {
            "uid": "sDhinqoIwHHc",
            "name": "activity_condition 1",
            "activity_type": null,
            "start_datetime": "2019-09-19T12:09:05.000+07:00",
            "end_datetime": "2019-09-20T12:08:43.000+07:00",
            "activity_volume": 1000,
            "user_type": "sansiri_family",
            "status": "active",
            "created_at": "2019-09-19T12:22:25.146+07:00",
            "updated_at": "2019-09-19T12:24:50.775+07:00",
            "activity_schedule_id": 2,
            "available_quota": 999,
            "activity_uid": "NB2sMQWstgQZ"
        }
    ],
    "activity_volume": 1000,
    "activity_available": 999,
    "activity_minimum_volume": 2,
    "location_map": "location",
    "created_at": "2019-09-19T11:36:47.433+07:00",
    "updated_at": "2019-09-19T16:36:08.565+07:00",
    "maximum_seats_per_user": 1
}
```

### HTTP Request

`PATCH /api/v1/client/${apiKey}/activities/${activityUid}/inactivate`

### Response

`TYPE: Object`

| Parameter | example        | Description            |
| --------- | -------------- | ---------------------- |
| status    | active | Activity status |
