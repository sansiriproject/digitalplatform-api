## activities/activities#create

```javascript
const request = require("request-promise");
const jwt = require("jsonwebtoken");

let apiKey = "apiKey";
let apiSecret = "apiSecret";
let activityUid = "sirnbiusASDIIH";

const hostname = "https://digitalplatform-api.dev.sansiriproject.com";
const apiPath = `/api/v1/client/${apiKey}/activities`;

let expTime = Math.floor(Date.now() / 1000) + 60; // expiration + 60 seconds
let token = jwt.sign({ api_key: apiKey, exp: expTime }, apiSecret);

let options = {
  method: "POST",
  uri: `${hostname}${apiPath}`,
  headers: {
    CMSAuthToken: `Bearer ${token}`
  },
  body: {
    "activity": {
        "name": "test client activity 102",
        "description": "description",
        "condition_detail": "condition",
        "location": "location",
        "shop_name": "Shop1",
        "activity_minimum_volume": 1,
        "prefix_booking_code": "SHP",
        "location_map": "https://goo.gl/maps/UNazaRq6pkYAjAns9",
        "maximum_seats_per_user": 1
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
    "uid": "CNXM7DtV2fG2",
    "id": 64,
    "name": "test client activity 102",
    "description": "description",
    "shop_name": "Shop1",
    "condition_detail": "condition",
    "location": "location",
    "status": "active",
    "running_number": "AT190040",
    "activity_conditions": [],
    "activity_volume": 0,
    "activity_available": 0,
    "activity_minimum_volume": 1,
    "location_map": "https://goo.gl/maps/UNazaRq6pkYAjAns9",
    "created_at": "2019-09-19T13:47:43.196+07:00",
    "updated_at": "2019-09-19T13:47:43.196+07:00",
    "maximum_seats_per_user": 1
}
```

This endpoint create participant for activityUid.
Please note that `member_firebase_uid` is from HSA Single Sign On

### HTTP Request

`POST /api/v1/client/${apiKey}/activities/${activityUid}/participants`

### Request Body

| Parameter           | example                | Description                          |
| ------------------- | ---------------------- | ------------------------------------ |
| name | client activity 102 | Activity Name |
| description | Description | Activity description |
| condition_detail | Condition details | Condition details |
| location | Sathorn | Location Name |
| shop_name | Shop1 | Shop Name |
| activity_minimum_volume | 1 | Minimum volume for this activity (Optional) |
| prefix_booking_code | PRE | Prefix 3 digits for participant booking ID running number |
| location_map | location map URL | location map URL |
| maximum_seats_per_user | 1 | Maximum seats per user for booking this activity |

### Response

`TYPE: Object`

| Parameter | example        | Description            |
| --------- | -------------- | ---------------------- |
| uid       | "cPsF-wBftDcs" | URL Safe Base64 String |
| description | "Description" | Activity description |
| shop_name | "Shop1" | Shop name |
| condition_detail | "Condition details" | Condition details |
| location | "Sathorn" | Location name |
| status    | "active" | Activity status |
| running_number  | "AT190040" | Activity ID |
| activity_conditions | "Condition details" | Condition details |
| activity_volume | "100" | Activity volume summary from all active condition |
| activity_available | "50" | Activity volume summary from all available seats |
| activity_minimum_volume | "1" | Minimum volume for this activity |
| location_map | "location map URL" | location map URL |
| maximum_seats_per_user | "1" | Maximum seats per user for booking this activity |
