## activities/participants#show

```javascript
const request = require("request-promise");
const jwt = require("jsonwebtoken");

let apiKey = "apiKey";
let apiSecret = "apiSecret";
let activityUid = "sirnbiusASDIIH";

const hostname = "https://digitalplatform-api.dev.sansiriproject.com";
const apiPath = `/api/v1/client/${apiKey}/activities/${activityUid}/activity_schedules/${activity_schedule_uid}/participants/${uid}`;

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
[
  {
      "uid": "uL6azx8TDKmv",
      "name": "name1",
      "user_type": "sansiri_family",
      "email": "khemmapon@mailinator.com",
      "telephone": "0886565880",
      "status": "attended",
      "created_at": "2019-09-19T12:52:49.642+07:00",
      "updated_at": "2019-09-19T13:00:21.348+07:00",
      "attended_datetime": "2019-09-19T13:00:21.354+07:00",
      "booking_code": "SHP20191974373",
      "seats_reserved": 1,
      "confirmed_datetime": "2019-09-19T12:59:44.714+07:00",
      "member": {
          "env": "dev",
          "uid": "q-eCTA9W7Fjw",
          "created_at": "2019-05-10T15:30:42.188+07:00",
          "updated_at": "2019-09-19T21:02:04.773+07:00",
          "firebase_login_type": "email",
          "member_type_list": [
              "sansiri_family"
          ],
          "main_member_type": "sansiri_family",
          "frontend_firebase_json": {
              "kind": "identitytoolkit#VerifyPasswordResponse",
              "email": "khemmapon@mailinator.com",
              "idToken": "eyJhbGciOiJSUzI1NiIsImtpZCI6IjgyZjBiNDZjYjc1OTBjNzRmNTNhYzdhOWUwY2IxYzAzMjRlY2RkNzUiLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJodHRwczovL3NlY3VyZXRva2VuLmdvb2dsZS5jb20vaHNhLWRldiIsImF1ZCI6ImhzYS1kZXYiLCJhdXRoX3RpbWUiOjE1NTc5ODE2MDgsInVzZXJfaWQiOiJQY0g3N3hzaHNLU0EzbDRyV3AyS0lDNlIzbTQzIiwic3ViIjoiUGNINzd4c2hzS1NBM2w0cldwMktJQzZSM200MyIsImlhdCI6MTU1Nzk4MTYwOCwiZXhwIjoxNTU3OTg1MjA4LCJlbWFpbCI6ImtoZW1tYXBvbkBtYWlsaW5hdG9yLmNvbSIsImVtYWlsX3ZlcmlmaWVkIjpmYWxzZSwiZmlyZWJhc2UiOnsiaWRlbnRpdGllcyI6eyJlbWFpbCI6WyJraGVtbWFwb25AbWFpbGluYXRvci5jb20iXX0sInNpZ25faW5fcHJvdmlkZXIiOiJwYXNzd29yZCJ9fQ.LJuMDsDmGv1XgWCuVd0NH4M7fqn81yCQ9kJhBtlakNwzaTWHawEjVN653JxhrlVjWBPQK4FdcKSByo5UahdoklcLI6rLBonoNKlDumEqp-25_2XJISp8aa_EWNUojq8zldDrxDQ2a88MLIOgUHUnb5EnkyYUbmJtVkczipXMFbZah9GoAm62FZfeiStdeswhCSUkwIQvEcn--2CVLL8CQPIm8UaDgEK3mbq3iwx8_lcCfvVyr3aIPOrP_Larbql2-RJJ6GdS3TgcAvvEhsxYgLTGwjrna38wBV1GV6e38Ng-Ucxl7iAtXQ6Bcb1_iTl_OrZ_rLdCxTVBQEmGGkmPJA",
              "localId": "PcH77xshsKSA3l4rWp2KIC6R3m43",
              "expiresIn": "3600",
              "registered": true,
              "displayName": "",
              "refreshToken": "AEu4IL0BIiwrZ6ZqClXv7guUcSDA4xeRLEeqSehWZ_TGi_8QJtyRj3dlS0JDWLKsL5vothkyrBAKgyGWsBx2Yh0LD7ov_2SSgiJIeSDBsA30jqPHxHPKBCov4DwXd8QyDXQ_9scblABE8o3X51s5lGf2P-9u_VnU0Mt1sbd12f_gaXuOr6f1TQf-70WmMbvsICylkn0lFm1x",
              "expirationTime": 1557985208
          },
          "profile": {
              "email": "khemmapon@mailinator.com",
              "mobile": "0886565880",
              "first_name": "ขงเบ้งน้อย",
              "last_name": "กรุ๊ป จำกัด",
              "local_first_name": "ขงเบ้งน้อย",
              "local_last_name": "กรุ๊ป จำกัด",
              "id_card_number": "0105559028702",
              "passport": null,
              "date_of_birth": "2019-09-19"
          },
          "profile_editable_fields": {
              "email": false,
              "mobile": true,
              "first_name": true,
              "last_name": true,
              "local_first_name": false,
              "local_last_name": false,
              "date_of_birth": true
          }
      },
      "activity_condition_uid": "sDhinqoIwHHc"
  }
]
```

This endpoint retrieves all participants from activity.

### HTTP Request

`PATCH /api/v1/client/${apiKey}/activities/${activityUid}/activity_schedules/${activity_schedule_uid}/participants/${uid}`

### Response

`TYPE: Array`

| Parameter         | example        | Description                           |
| ----------------- | -------------- | ------------------------------------- |
| uid               | "cPsF-wBftDcs" | URL Safe Base64 String                |
| name               | "name1" | members name String                |
| user_type              | "sansiri_family" | sansiri_family, sansiri_priority |
| email               | "khemmapon@mailinator.com" | email login
| telephone           | "0886565880" |                  |
| status            | "attending"    | attending,confirm,attended,canceled       |
| attended_datetime | "2019-09-19T13:00:21.354+07:00" | time stamp when attendance is checked |
| booking_code | "SHP20191974373" |  |
| seats_reserved |       1         | seats reserved count |
| confirmed_datetime |  "2019-09-19T12:59:44.714+07:00"  | time stamp when confirm is checked |
