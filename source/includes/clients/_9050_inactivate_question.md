## activities/question#inactivate

```javascript
const request = require("request-promise");
const jwt = require("jsonwebtoken");

let apiKey = "apiKey";
let apiSecret = "apiSecret";
let activityUid = "sirnbiusASDIIH";

const hostname = "https://digitalplatform-api.dev.sansiriproject.com";
const apiPath = `/api/v1/client/${apiKey}/activities/:activity_uid/activity_schedules/${activityUid}/activity_conditions/${uid}/inactivate`;


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
  "uid": "YdfqgsybLQFG",
  "question_text": "Hi",
  "status": "inactive",
  "question_type": "text",
  "is_multiple": true,
}
```

### HTTP Request

`PATCH /api/v1/client/${apiKey}/activities/:activity_uid/activity_schedules/${activityUid}/activity_conditions/${uid}/inactivate`

### Response

`TYPE: Object`

| Parameter | example        | Description            |
| --------- | -------------- | ---------------------- |
| status    | inactive | active, inactive |
