## activities/participants#attend

```javascript
const request = require("request-promise");
const jwt = require("jsonwebtoken");

let apiKey = "apiKey";
let apiSecret = "apiSecret";
let activityUid = "sirnbiusASDIIH";
let participantUid = "cPsF-wBftDcs";

const hostname = "https://digitalplatform-api.dev.sansiriproject.com";
const apiPath = `/api/v1/client/${apiKey}/activities/${activityUid}/participants/${participantUid}/attend`;

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
  "uid": "cPsF-wBftDcs",
  "name": "ชอร์ตง ฮอง นายโฮยิน ฮอง",
  "user_type": "all_user",
  "email": null,
  "telephone": null,
  "status": "attended",
  "created_at": "2019-04-23T03:20:44.388Z",
  "updated_at": "2019-04-23T03:20:44.388Z",
  "attended_datetime": null,
  "activity_condition": {
    "uid": "0_5eB6GXz3Wc",
    "name": "GARDEN - All Users",
    "activity_type": null,
    "start_datetime": "2019-04-03T18:28:00.000Z",
    "end_datetime": "2019-05-30T18:28:00.000Z",
    "activity_volume": 500,
    "user_type": "all_user",
    "status": "active",
    "created_at": "2019-04-18T18:28:15.957Z",
    "updated_at": "2019-04-18T18:28:15.957Z"
  }
}
```

This endpoint update participant `participantUid` status to `attended`.

> Only `attending` can be transitioned to `comfirmed`,`attended`. `canceled` cannot be toggle to attended to prevent over capacity booking.

API validates that `participantUid` belongs to `activityUid`.

### HTTP Request

`PATCH /api/v1/client/${apiKey}/activities/${activityUid}/participants/${participantUid}/attend`

### Response

`TYPE: Object`

| Parameter | example        | Description            |
| --------- | -------------- | ---------------------- |
| uid       | "cPsF-wBftDcs" | URL Safe Base64 String |
| status    | "attended"     |                        |
