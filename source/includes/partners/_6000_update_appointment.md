## 2.4 Update Appointment

```javascript
const request = require("request-promise");

let token = "token_from_previous_section";
let locale = "en"; // en, th, zh
const hostname = "https://family.sansiri.com";
const apiPath = `/family/{locale}/service/booking/confirm/update`;

let options = {
  method: "POST",
  uri: `${hostname}${apiPath}`,
  body: {
    token: token,
    status: "COMPLETED",
    order_id: "partner-a-20190511-001",
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

Use this api to update appointment. The updatable fields are listed below.

`POST https://family.sansiri.com/family/{locale}/service/booking/confirm/update`

Parameter `in POST BODY`

| Field             | Type   | Description                                                                                              |
| ----------------- | ------ | -------------------------------------------------------------------------------------------------------- |
| token             | string | a unique string represent specific service appointment record at Sansiri's.                              |
| status            | string | the current of the transaction at service provider site. Allowed values: COMPLETED, CONFIRMED, CANCELLED |
| order_id optional | string | the transaction id / order represent the transaction / order at service provider site                    |
| data optional     | string | a json string / object containing any other information not belongs to any other fields                  |
