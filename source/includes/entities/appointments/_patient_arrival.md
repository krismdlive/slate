## Appointments - Patient Arrival

```shell
curl -v -X PUT {server_url}/api/v1/patients/{patient_id}/appointments/{appointment_id}/entered_waiting_room \
  -H 'Authorization: Bearer {jwt_token}' \
  -d ''
```

```ruby
RestClient::Request.new(
  :method => :put,
  :url => '{server_url}/api/v1/patients/{patient_id}/appointments/{appointment_id}/entered_waiting_room',
  :headers => {
    'Authorization' => 'Bearer {jwt_token}'
  }
).execute
```

> The above command returns 200 OK with no content.

This call is used to notify a provider that a patient has arrived to an appointment.

### HTTP Request

To notify the provider that a patient has arrived to the appointment, make a request to:

`POST {server_url}/api/v1/patients/{patient_id}/appointments/{appointment_id}/entered_waiting_room`

### Headers

Parameter     | Default
--------------|------------------------
Authorization | Bearer {jwt_token}

This request must include a valid User JWT token, please see our [documentation](#user-tokens).

### URL Parameters

The following parameters need to be included in the URL of the request:

Attribute      | Required | Description
---------------|----------|----------------------
patient_id     | true     | MDLIVE ID for patient
appointment_id | true     | MDLIVE ID for appointment
