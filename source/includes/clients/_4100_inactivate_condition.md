## activities/activities#activate

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
      "activity_schedule_id": 2,
      "uid": "sDhinqoIwHHc",
      "name": "activity_condition 1",
      "activity_type": null,
      "start_datetime": "2019-09-19T12:09:05.000+07:00",
      "end_datetime": "2019-09-20T12:08:43.000+07:00",
      "activity_volume": 1000,
      "user_type": "sansiri_family",
      "status": "inactive",
      "created_at": "2019-09-19T12:22:25.146+07:00",
      "updated_at": "2019-09-20T10:13:47.954+07:00",
      "available_quota": 999,
      "activity_uid": "NB2sMQWstgQZ"
}
```

### HTTP Request

`PATCH /api/v1/client/${apiKey}/activities/${activityUid}/inactivate`

### Response

`TYPE: Object`

| Parameter | example        | Description            |
| --------- | -------------- | ---------------------- |
| status    | inactive | condition status |
