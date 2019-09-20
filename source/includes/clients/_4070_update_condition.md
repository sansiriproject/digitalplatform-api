## activities/condition#update

```javascript
const request = require("request-promise");
const jwt = require("jsonwebtoken");

let apiKey = "apiKey";
let apiSecret = "apiSecret";

const hostname = "https://digitalplatform-api.dev.sansiriproject.com";
const apiPath = `/api/v1/client/${apiKey}/activities/${activity_uid}/activity_schedules/${activity_schedule_uid}/activity_conditions/${uid}`;

let expTime = Math.floor(Date.now() / 1000) + 60; // expiration + 60 seconds
let token = jwt.sign({ api_key: apiKey, exp: expTime }, apiSecret);

let options = {
  method: "POST",
  uri: `${hostname}${apiPath}`,
  headers: {
    CMSAuthToken: `Bearer ${token}`
  },
  body: {
	"activity_condition": {
    	"name": "activity_condition 1",
    	"start_datetime": "2019-09-19T12:09:05+07:00",
    	"end_datetime": "2019-09-20T12:08:43+07:00",
    	"activity_volume": 1000,
    	"user_type": "sansiri_family"
	        }
        }
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
      "updated_at": "2019-09-19T21:02:04.322+07:00",
      "available_quota": 999,
      "activity_uid": "NB2sMQWstgQZ"
  }
]
```

This endpoint retrieves all activites.

#### HTTP Request

`POST /api/v1/client/${apiKey}/activities/${activity_uid}/activity_schedules/${activity_schedule_uid}/activity_conditions/${uid}`

### Request Body

| Parameter           | example                | Description                          |
| ------------------- | ---------------------- | ------------------------------------ |
| name | "activity_condition 1" |     Condition Name  |
| start_datetime          | "2019-09-19T12:09:05.000+07:00" |  Condition start date  |
| end_datetime   | "2019-09-20T12:08:43.000+07:00"  |   Condition end date |
| activity_volume    | "1000" | Total availability for this condition              |
| user_type | "sansiri_family" | Sansiri family user type |



#### Response

`TYPE: Array`

| Parameter          | example      | Description                       |
| ------------------ | ------------ | --------------------------------- |
| uid  | "asdfuirtXX" | URL Safe Base64 String |
| name | "activity_condition 1" |     Condition Name  |
| start_datetime          | "2019-09-19T12:09:05.000+07:00" |  Condition start date  |
| end_datetime   | "2019-09-20T12:08:43.000+07:00"  |   Condition end date |
| activity_volume    | "1000" | Total availability for this condition              |
| user_type | "sansiri_family" | Sansiri family user type |
| available_quota | "999" | Available quota for this condition |
| activity_uid | "NB2sMQWstgQZ" | URL Safe Base64 String |
