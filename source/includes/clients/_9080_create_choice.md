## activities/choice#create

```javascript
const request = require("request-promise");
const jwt = require("jsonwebtoken");

let apiKey = "apiKey";
let apiSecret = "apiSecret";

const hostname = "https://digitalplatform-api.dev.sansiriproject.com";
const apiPath = `/api/v1/client/${apiKey}/activities/${activity_uid}/questions/${question_uid}/choices`;

let expTime = Math.floor(Date.now() / 1000) + 60; // expiration + 60 seconds
let token = jwt.sign({ api_key: apiKey, exp: expTime }, apiSecret);

let options = {
  method: "POST",
  uri: `${hostname}${apiPath}`,
  headers: {
    CMSAuthToken: `Bearer ${token}`
  },
  body: {
    "choice": {
  		"choice_text": "Hello"
  	}
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
       "uid": "88p1vWn5Y9Ti",
       "choice_text": "Hello",
  }
]
```

This endpoint retrieves all activites.

#### HTTP Request

`POST /api/v1/client/${apiKey}/activities/${activity_uid}/questions/${question_uid}/choices`

### Request Body

| Parameter           | example                | Description                          |
| ------------------- | ---------------------- | ------------------------------------ |
| uid  | "asdfuirtXX" | URL Safe Base64 String |
| choice_text | "q2" | choice text |




#### Response

`TYPE: Array`

| Parameter          | example      | Description                       |
| ------------------ | ------------ | --------------------------------- |
| uid  | "asdfuirtXX" | URL Safe Base64 String |
| choice_text | "q2" | choice text |
