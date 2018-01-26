## Appointments - Video Consultations in Browser

```shell
curl -X GET {server_url}/api/v1/appointments/{appointment_id}/connection_params \
  -H 'Authorization: Bearer: {jwt_token}' \
  -H 'Accept: application/json'
```

```ruby
RestClient::Request.new(
  :method => :get,
  :url => '{server_url}/api/v1/appointments/{appointment_id}/connection_params',
  :headers => {
    'Authorization' => 'Bearer {jwt_token}',
    'Accept' => 'application/json'
  }
).execute
```

> The above command returns JSON structured like this:

```json
{
  "patient_id":4,
  "provider_id":36,
  "start_time":"2018-01-27T16:00:00.000Z",
  "end_time":"2018-01-27T16:30:00.000Z",
  "url":"https://patients.mdlive.com/appointments/1?signature=?signature=2a28d944aa28e63ec0d0d636cc22d801a660a12092399e43a208378902c78d91"}
```

This call is used to fetch information about a video consultation, including the url to the page that allows patients to join. Going to the url specified in the response automatically registers the [patient_arrival](#appointments-patient-arrival).

### HTTP Request

To fetch information about a video consultation, including the url to the page that allows patients to join, make a request to:

`GET {server_url}/api/v1/appointments/{appointment_id}/connection_params`

### Headers

Parameter     | Default
--------------|------------------------
Authorization | Bearer {jwt_token}
Accept        | application/json

This request must include a valid User JWT token, please see our [documentation](#user-tokens).

### URL Parameters

The following parameters need to be included in the URL of the request:

Attribute      | Required | Description
---------------|----------|----------------------
appointment_id | true     | MDLIVE ID for appointment
