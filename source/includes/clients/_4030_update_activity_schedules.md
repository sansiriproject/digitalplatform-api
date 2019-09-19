## activities/activity_schedules#create

```javascript
const request = require("request-promise");
const jwt = require("jsonwebtoken");

let apiKey = "apiKey";
let apiSecret = "apiSecret";
let activityUid = "sirnbiusASDIIH";

const hostname = "https://digitalplatform-api.dev.sansiriproject.com";
const apiPath = `/api/v1/client/:api_key/activities/${activity_uid}/activity_schedules`;

let expTime = Math.floor(Date.now() / 1000) + 60; // expiration + 60 seconds
let token = jwt.sign({ api_key: apiKey, exp: expTime }, apiSecret);

let options = {
  method: "POST",
  uri: `${hostname}${apiPath}`,
  headers: {
    CMSAuthToken: `Bearer ${token}`
  },
  body: {
    "activity_schedule": {
  		"start_datetime": "2019-09-19T12:09:05+07:00",
      	"end_datetime": "2019-09-20T12:08:43+07:00",
      	"description": "description",
      	"maximum_seats_per_user": 1
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
{
  "uid": "kGQM4hOvO-__",
  "id": 43,
  "start_datetime": "2019-09-19T12:09:05.000+07:00",
  "end_datetime": "2019-09-20T12:08:43.000+07:00",
  "description": "description",
  "created_at": "2019-09-19T17:26:25.543+07:00",
  "updated_at": "2019-09-19T17:26:25.543+07:00",
  "created_by": null,
  "updated_by": null,
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
| start_datetime | "2019-09-19T12:09:05.000+07:00"  | Schedule start date/time |
| end_datetime | "2019-09-20T12:08:43.000+07:00"  | Schedule end date/time |
| description |  "description" |                   |
| maximum_seats_per_user  | "2" |   


### Response

`TYPE: Object`

| Parameter | example        | Description            |
| --------- | -------------- | ---------------------- |
| uid | "asdfuirtXX" | URL Safe Base64 String  |   
| start_datetime | "2019-09-19T12:09:05.000+07:00"  | Schedule start date/time |
| end_datetime | "2019-09-20T12:08:43.000+07:00"  | Schedule end date/time |
| description |  "description" |                   |
| maximum_seats_per_user  | "2" |                   |
