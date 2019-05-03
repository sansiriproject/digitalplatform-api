## Get one Activity form UID

```javascript
const request = require("request-promise");
const jwt = require("jsonwebtoken");

let apiKey = "apiKey";
let apiSecret = "apiSecret";
let activityUid = "sirnbiusASDIIH";

const hostname = "https://digitalplatform-api.dev.sansiriproject.com";
const apiPath = `/api/v1/client/${apiKey}/activities/${activityUid}`;

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
{
  "locale": "en",
  "client_uid": "171s_vNNF9yI",
  "uid": "fLxeDNuLY6Z2",
  "id": 30,
  "name": "GARDEN PLANTING",
  "description": null,
  "shop_name": null,
  "condition_detail": null,
  "location": "BANGKOK",
  "status": "active",
  "running_number": "AT190030",
  "activity_conditions": [
    {
      "uid": "0_5eB6GXz3Wc",
      "name": "GARDEN - All Users",
      "activity_type": null,
      "start_datetime": "2019-04-03T18:28:00.000Z",
      "end_datetime": "2019-05-30T18:28:00.000Z",
      "activity_volume": 500,
      "user_type": "all_user",
      "status": "active",
      "activity_id": 30,
      "created_at": "2019-04-18T18:28:15.957Z",
      "updated_at": "2019-04-18T18:28:15.957Z",
      "usage_type": "per_user",
      "usage_volume": 500,
      "available_quota": 498,
      "activity_uid": "fLxeDNuLY6Z2"
    }
  ],
  "activity_volume": 500,
  "activity_available": 498
}
```

This endpoint retrieves all kittens.

### HTTP Request

`GET /api/v1/client/${apiKey}/activities/${activityUid}`

<aside class="success">
Remember — a happy api require `activityUid`.
</aside>

### Response

`TYPE: Object`

| Parameter          | example      | Description                       |
| ------------------ | ------------ | --------------------------------- |
| uid                | "asdfuirtXX" | URL Safe Base64 String            |
| name               | ""           |                                   |
| description        | ""           |                                   |
| shop_name          | ""           |                                   |
| condition_detail   | ""           |                                   |
| location           | ""           |                                   |
| activity_volume    | 100          | Total availability                |
| activity_available | 99           | space left                        |
| running_number     | ATXXXXXX     | Activity Running number / code    |
| user_type          | all_user     | priority,family,employee,all_user |
