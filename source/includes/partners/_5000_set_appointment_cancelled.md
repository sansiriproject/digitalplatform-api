## 2.3 Cancel Appointment

```javascript
const request = require("request-promise");

let token = "token_from_previous_section";
let locale = "en"; // en, th, zh
const hostname = "https://family.sansiri.com";
const apiPath = `/family/{locale}/service/booking/confirm/error`;

let options = {
  method: "POST",
  uri: `${hostname}${apiPath}`,
  body: {
    token: token,
    message: "customer lost interest",
    data: {
      foo: "far"
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
  "status": 200,
  "code": "OK",
  "current_status": "CANCELLED"
}
```

Use this api to set appointment to cancelled. This will tell Sansiri that the specific request has been cancelled or unfulfilled on Partner system.

`POST https://family.sansiri.com/family/{locale}/service/booking/confirm/error`

Parameter `in POST BODY`

| Field            | Type   | Description                                                                             |
| ---------------- | ------ | --------------------------------------------------------------------------------------- |
| token            | string | a unique string represent specific service appointment record at Sansiri's.             |
| message optional | string | any string the service provider would like to be store at Sansiri's                     |
| data optional    | string | a json string / object containing any other information not belongs to any other fields |
