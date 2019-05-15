## 2.2 Complete or Confirm Appointment

```javascript
const request = require("request-promise");

let token = "token_from_previous_section";
let locale = "en"; // en, th, zh
const hostname = "https://family.sansiri.com";
const apiPath = `/family/${locale}/service/booking/confirm/success`;

let options = {
  method: "POST",
  uri: `${hostname}${apiPath}`,
  body: {
    token: token,
    status: "COMPLETED",
    message: "customer has made payment",
    order_id: "partner-a-20190511-001",
    order_date: "2019-05-11T18:28:00.000Z",
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
  "current_status": "COMPLETED"
}
```

Use this api to set appointment to completed or confirmed. This will tell Sansiri that the specific request has been completed on Partner system.

`POST https://family.sansiri.com/family/{locale}/service/booking/confirm/success`

Parameter `in POST BODY`

| Field               | Type   | Description                                                                                   |
| ------------------- | ------ | --------------------------------------------------------------------------------------------- |
| token               | string | a unique string represent specific service appointment record at Sansiri's.                   |
| status              | string | the current of the transaction at service provider site. Allowed values: COMPLETED, CONFIRMED |
| message optional    | string | any string the service provider would like to be store at Sansiri's                           |
| order_id optional   | string | the transaction id / order represent the transaction / order at service provider site         |
| order_date optional | string | the date/time when the order has occurred (ISO8601 format)                                    |
| data optional       | string | a json string / object containing any other information not belongs to any other fields       |
