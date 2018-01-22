## Appointments - Cancel

```shell
curl -X PUT {server_url}/api/v1/patients/{patient_id}/appointments/{appointment_id}/cancel \
  -H 'Authorization: Bearer {jwt_token}' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'
```

```ruby
RestClient::Request.new(
  :method => :put,
  :url => '{server_url}/api/v1/patients/{patient_id}/appointments/{appointment_id}/cancel',
  :headers => {
    'Authorization' => 'Bearer {jwt_token}',
    'Content-type'  => 'application/json',
    'Accept'  => 'application/json',
  }
).execute
```

> The above command returns a `204 NO CONTENT` response.

To cancel a patient's appointment, make a request to:


### HTTP Request

`PUT {server_url}/api/v1/patients/{patient_id}/appointments/{appointment_id}/cancel`


### Headers

Parameter     | Default
--------------|------------------------
Authorization | Bearer {jwt_token}
Content-type  | application/json
Accept        | application/json

This request must include a valid User JWT token, please see our [documentation](#user-tokens).


### URL Parameters

The following parameters need to be included in the URL of the request:

Attribute      | Required | Description
---------------|----------|----------------------
patient_id     | true     | MDLIVE ID for patient
appointment_id | true     | ID of patient's appointment
