## 1. Redirecting to partner site

This section is `Sansiri Family` redirecting to `Partner Site`. We require `Partner URL` for us to redirect via `GET` or send data via `POST`.

1. For example, our partners are required to send us either on of these information.
   1. Partner A using `GET`
      1. Method: `GET`
      1. URL: `https://www.partner-A.com/sansiri-family`
   1. Partner B using `POST`
      1. Method: `POST`
      1. URL: `https://www.partner-B.com/sansiri-family`

### Sansiri family to Partner

Once we configured our system to be able to send data to partner site. Please follow the guideline below to integrate the two systems.

1. Each request will be sent through a form, using either GET or POST method, as chosen by the service provider.
1. Each request will always have "Primary Parameter".
1. Only "POST" request will include the detailed information
1. Unless opt-out, each request can contain the user profile.
1. Unless opt-out, each request can contain an "ORIGIN ADDRESS", "DESTINATION ADDRESS", or both, depends on the nature of the provided service itself
1. Custom parameters can also be included on the basis of each service provider
1. All of the information can also be retrieve via "Get an appointment" using the provided access_token later

### VIA GET

`GET https://www.partner-A.com/sansiri-family`

Primary Parameter `in Query String`

| Field                        | Type   | Description                                                                                                                                                                                                                                                        |
| ---------------------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| token                        | string | a unique string represent specific service appointment record at Sansiri's. This will be used for updating the reservation status later on.                                                                                                                        |
| access_token                 | string | a unique string, short lived access token, generated for each request sent to the partner site. The partner system should use this access token to verified the validity of the request, by sending the access token back to Sansiri via the "Get Appointment" api |
| access_token_expired_at      | string | the date / time which the access token will be expired                                                                                                                                                                                                             |
| access_token_expired_seconds | number | the number of seconds before the access token would be expired                                                                                                                                                                                                     |
| uuid                         | string | a unique string represent a certain user / member at Sansiri's. This will always be the same for each user.                                                                                                                                                        |
| lang                         | string | the locale which the user was using                                                                                                                                                                                                                                |
| return_url                   | string | the url which the user should be redirected to if the appointment could be considered as SUCCESS at the partner site                                                                                                                                               |
| error_url                    | string | the url which the user should be redirected to if the appointment could be considered as ERROR or CANCELLED at the partner site                                                                                                                                    |

### VIA POST

`POST https://www.partner-B.com/sansiri-family`

### Primary Parameter `in Request BODY`

| Field                        | Type   | Description                                                                                                                                                                                                                                                        |
| ---------------------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| token                        | string | a unique string represent specific service appointment record at Sansiri's. This will be used for updating the reservation status later on.                                                                                                                        |
| access_token                 | string | a unique string, short lived access token, generated for each request sent to the partner site. The partner system should use this access token to verified the validity of the request, by sending the access token back to Sansiri via the "Get Appointment" api |
| access_token_expired_at      | string | the date / time which the access token will be expired                                                                                                                                                                                                             |
| access_token_expired_seconds | number | the number of seconds before the access token would be expired                                                                                                                                                                                                     |
| uuid                         | string | a unique string represent a certain user / member at Sansiri's. This will always be the same for each user.                                                                                                                                                        |
| lang                         | string | the locale which the user was using                                                                                                                                                                                                                                |
| return_url                   | string | the url which the user should be redirected to if the appointment could be considered as SUCCESS at the partner site                                                                                                                                               |
| error_url                    | string | the url which the user should be redirected to if the appointment could be considered as ERROR or CANCELLED at the partner site                                                                                                                                    |

### Member info only if available

| Field        | Type   | Description                                |
| ------------ | ------ | ------------------------------------------ |
| first_name   | string | the user first name                        |
| last_name    | string | the user last name                         |
| phone_number | string | the user phone number                      |
| email        | string | the user email                             |
| project_id   | string | related project id of the consumer address |
| project_name | string | related project name the consumer address  |
| model_code   | string | related model code of the consumer address |
| model_id     | string | related model id of the consumer address   |
| model_name   | string | related model name of the consumer address |

### Origin Address if available

| Field                      | Type   | Description                                |
| -------------------------- | ------ | ------------------------------------------ |
| origin_address             | string | the full text of the origin address        |
| origin_address_1           | string | the address 1 text of the origin address   |
| origin_address_2           | string | the address 2 text of the origin address   |
| origin_address_street      | string | the street address of the origin address   |
| origin_address_district    | string | the district name of the origin address    |
| origin_address_subdistrict | string | the subdistrict name of the origin address |
| origin_address_province    | string | the province name of the origin address    |
| origin_address_postal_code | string | the postal code of the origin address      |

### Destination Address if available

| Field                           | Type   | Description                                     |
| ------------------------------- | ------ | ----------------------------------------------- |
| destination_address             | string | the full text of the destination address        |
| destination_address_1           | string | the address 1 text of the destination address   |
| destination_address_2           | string | the address 2 text of the destination address   |
| destination_address_street      | string | the street address of the destination address   |
| destination_address_district    | string | the district name of the destination address    |
| destination_address_subdistrict | string | the subdistrict name of the destination address |
| destination_address_province    | string | the province name of the destination address    |
| destination_address_postal_code | string | the postal code of the destination address      |
