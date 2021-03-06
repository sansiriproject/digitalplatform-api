## activities/question#update

```javascript
const request = require("request-promise");
const jwt = require("jsonwebtoken");

let apiKey = "apiKey";
let apiSecret = "apiSecret";

const hostname = "https://digitalplatform-api.dev.sansiriproject.com";
const apiPath = `/api/v1/client/${apiKey}/activities/${activity_uid}/questions/${uid}`;

let expTime = Math.floor(Date.now() / 1000) + 60; // expiration + 60 seconds
let token = jwt.sign({ api_key: apiKey, exp: expTime }, apiSecret);

let options = {
  method: "PATCH",
  uri: `${hostname}${apiPath}`,
  headers: {
    CMSAuthToken: `Bearer ${token}`
  },
  body: {
	   "question": {
		      "question_text": "Hello",
    	    "question_type": "text",
    	    "is_multiple": false,
    	    "sorting_index": 1.0
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
    "uid": "fwJ7QGg2-fr1",
    "question_text": "Hello",
    "status": "active",
    "question_type": "text",
    "is_multiple": false,
  }
]
```

This endpoint retrieves all activites.

#### HTTP Request

`PATCH /api/v1/client/${apiKey}/activities/${activity_uid}/questions/${uid}`

### Request Body

| Parameter           | example                | Description                          |
| ------------------- | ---------------------- | ------------------------------------ |
| uid  | "asdfuirtXX" | URL Safe Base64 String |
| question_text | "q2" | question text |
| question_type   | "text"  |   checkbox, radio, text |
| is_multiple    | false | true, false |
| sorting_index          | 1.0 |  decimal  |



#### Response

`TYPE: Array`

| Parameter          | example      | Description                       |
| ------------------ | ------------ | --------------------------------- |
| uid  | "asdfuirtXX" | URL Safe Base64 String |
| question_text | "q2" | question text |
| status          | "active" |  active, inactive  |
| question_type   | "text"  |   checkbox, radio, text |
| is_multiple    | false | true, false |
