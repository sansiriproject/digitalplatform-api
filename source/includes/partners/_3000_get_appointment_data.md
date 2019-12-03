## 2.1 Get Appointment Data

```javascript
const request = require("request-promise");

let access_token = "access_token_from_previous_section";
const hostname = "https://family.sansiri.com";
const apiPath = `/family/api/booking/appointment?access_token=${access_token}`;

let options = {
  uri: `${hostname}${apiPath}`,
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

Example Response

```json
{
  "uuid": "uuid",
  "first_name": "first_name",
  "last_name": "last_name",
  "phone_number": "phone_number",
  "email": "email",
  "date_of_birth": "date_of_birth",
  "project_id": "project_id",
  "project_name": "project_name",
  "model_code": "model_code",
  "model_id": "model_id",
  "model_name": "model_name",
  "origin_address": "origin_address",
  "origin_address_1": "origin_address_1",
  "origin_address_2": "origin_address_2",
  "origin_address_district": "origin_address_district",
  "origin_address_sub_district": "origin_address_sub_district",
  "origin_address_province": "origin_address_province",
  "origin_address_postal_code": "origin_address_postal_code",
  "destination_address": "destination_address",
  "destination_address_1": "destination_address_1",
  "destination_address_2": "destination_address_2",
  "destination_address_district": "destination_address_district",
  "destination_address_sub_district": "destination_address_sub_district",
  "destination_address_province": "destination_address_province",
  "destination_address_postal_code": "destination_address_postal_code",
  "return_url": "return_url",
  "error_url": "error_url",
  "update_url": "update_url",
  "addresses": [
    {
      "address": "address",
      "address_data": {
        "amphor": "amphor",
        "postCode": "postCode",
        "province": "province",
        "street": "street",
        "tambol": "tambol"
      },
      "code": "code",
      "model": {
        "code": "code",
        "id": "id",
        "name": "name"
      },
      "project": {
        "amphor": "amphor",
        "id": "id",
        "name": "name",
        "nameEn": "nameEn",
        "code": "code",
        "province": "province",
        "segment": "segment",
        "street": "street",
        "tambol": "tambol",
        "product": "product",
        "id": "id",
        "name": "name"
      },
      "project_name": "project_name",
      "project_name_en": "project_name_en",
      "room_no": "room_no",
      "usageArea": "usageArea"
    }
  ],
  "success": 1,
  "code": 200,
  "message": null
}
```

With this API, our Partner can fetrch the information of a given appointment, using `access_token` provided by Sansiri (please refer to this section <a href="#1-redirecting-to-partner-site">1. Redirecting to partner site</a>).

`GET https://family.sansiri.com/family/api/booking/appointment`

Parameter `in Query String`

| Field        | Type   | Description                                                                                   |
| ------------ | ------ | --------------------------------------------------------------------------------------------- |
| access_token | string | Access token from <a href="#1-redirecting-to-partner-site">1. Redirecting to partner site</a> |

Response, Please see data structure on the right for clearer picture.

| Field                             | Type   | Description                                                                           |
| --------------------------------- | ------ | ------------------------------------------------------------------------------------- |
| data                              | object | the response data                                                                     |
| -uuid                             | string | the user uuid                                                                         |
| -first_name                       | string | the user first_name                                                                   |
| -last_name                        | string | the user last_name                                                                    |
| -phone_number                     | string | the user phone number                                                                 |
| -project_id                       | string | the project id of the chosen address                                                  |
| -project_name                     | string | the project name of the chosen address                                                |
| -model_code                       | string | the code of the unit type of chosen address                                           |
| -model_id                         | string | the id of the unit type of chosen address                                             |
| -model_name                       | string | the name of the unit type of chosen address                                           |
| -origin_address                   | string | the full address of the origin address                                                |
| -origin_address_1                 | string | the main address of the origin address                                                |
| -origin_address_2                 | string | the sub address of the origin address                                                 |
| -origin_address_district          | string | the district name of the origin address                                               |
| -origin_address_sub_district      | string | the sub district name of the origin address                                           |
| -origin_address_province          | string | the province name of the origin address                                               |
| -origin_address_postal_code       | string | the postal code of the origin address                                                 |
| -destination_address              | string | the full address of the destination address                                           |
| -destination_address_1            | string | the main address of the destination address                                           |
| -destination_address_2            | string | the sub address of the destination address                                            |
| -destination_address_district     | string | the district name of the destination address                                          |
| -destination_address_sub_district | string | the sub district name of the destination address                                      |
| -destination_address_province     | string | the province name of the destination address                                          |
| -destination_address_postal_code  | string | the postal code of the destination address                                            |
| -return_url                       | string | the url which the service should post the information to, when the order is completed |
| -error_url                        | string | the url which the service should post the information to, when the order is canceled  |
| -update_url                       | string | the url which the service could post the information to update the order              |
| -addresses                        | array  | list of addresses available for the user                                              |
| --address                         | string | the address text                                                                      |
| --address_data                    | object | the address information separated by type                                             |
| ---amphor                         | string | the district name                                                                     |
| ---postCode                       | string | the postal code                                                                       |
| ---province                       | string | the province name                                                                     |
| ---street                         | string | the street name                                                                       |
| ---tambol                         | string | the subdistrict name                                                                  |
| --code                            | string |                                                                                       |
| --model                           | object | the unit type of the address                                                          |
| ---code                           | string |                                                                                       |
| ---id                             | string |                                                                                       |
| ---name                           | string |                                                                                       |
| --project                         | object | the project which the address belongs to                                              |
| ---amphor                         | string | the district name of the project                                                      |
| ---id                             | string | the project id                                                                        |
| ---name                           | string | the TH name of the project                                                            |
| ---nameEn                         | string | the EN name of the project                                                            |
| ---code                           | string | the zip code of the project                                                           |
| ---province                       | string | the province name of the project                                                      |
| ---segment                        | string |                                                                                       |
| ---street                         | string | the street name of the project                                                        |
| ---tambol                         | string | the sub district name of the project                                                  |
| ---product                        | object | the type of the project                                                               |
| ----id                            | string |                                                                                       |
| ----name                          | string |                                                                                       |
| --project_name                    | string | the TH name of the project                                                            |
| --project_name_en                 | string | the EN name of the project                                                            |
| --room_no                         | string | the room number of the address                                                        |
| --usageArea                       | string | the size of the address in square metres                                              |
| -success                          | number | Allowed values: 0, 1                                                                  |
| -message                          | string |                                                                                       |
