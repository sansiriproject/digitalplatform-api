## Authentication

> To authorize, check this example:

```javascript
const request = require("request-promise");
const jwt = require("jsonwebtoken");

let apiKey = "apiKey";
let apiSecret = "apiSecret";

const hostname = "https://digitalplatform-api.dev.sansiriproject.com";
const apiPath = "/api/v1/client/${apiKey}/some/api/path";

let expTime = Math.floor(Date.now() / 1000) + 60; // expiration + 60 seconds
let token = jwt.sign({ api_key: apiKey, exp: expTime }, apiSecret);

let options = {
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

> Make sure to replace `apiKey` with your API key and `apiSecret` with your API Secret.

Digital Platform api use JWT to secure all it APIs. Please contact Sansiri for apiKey and apiSecret.

With apiKey, generate JWT with this payload

`payload = { api_key: apiKey, exp: Time.now.to_i + 1.minute }`

With the payload above, sign it with JWT Secret.

`let token = jwt.sign(payload, apiSecret);`

Include token in every request header for each of your api call.

`CMSAuthToken: Bearer token`

There is an example on the right written in NodeJS using `request`, `request-promise`, and `jsonwebtoken` packages.

<aside class="notice">
Make sure to replace <code>json.web.token</code> with JWT generated from <code>apiKey</code> and <code>`apiSecret`</code> with 1 minute expiry.
</aside>
