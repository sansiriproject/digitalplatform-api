## activities/answer#index

```javascript
const request = require("request-promise");
const jwt = require("jsonwebtoken");

let apiKey = "apiKey";
let apiSecret = "apiSecret";

const hostname = "https://digitalplatform-api.dev.sansiriproject.com";
const apiPath = `/api/v1/client/${apiKey}/activities/${activity_uid}/questions/${question_uid}/answers`;

let expTime = Math.floor(Date.now() / 1000) + 60; // expiration + 60 seconds
let token = jwt.sign({ api_key: apiKey, exp: expTime }, apiSecret);

let options = {
  method: "GET",
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
      "uid": "dLDMvE-iZZm6",
          "answer_json_data": {
            "choice_uid": "tWASdHKnRlg5",
            "choice_text": "Hello"
     },
  }
]
```

This endpoint retrieves all activites.

#### HTTP Request

`GET /api/v1/client/${apiKey}/activities/${activity_uid}/questions/${question_uid}/answers`

#### Response

`TYPE: Array`

| Parameter          | example      | Description                       |
| ------------------ | ------------ | --------------------------------- |
| uid  | "asdfuirtXX" | URL Safe Base64 String |
| choice_uid  | "tWASdHKnRlg5" | URL Safe Base64 String |
| choice_text | "q2" | choice text |
