## Appointments - List Upcoming

The list of appointments returned as upcoming include all future appointments as well as any appointment within the last 60 minutes.

```shell
curl -X GET {server_url}/api/v2/patients/{patient_id}/appointments/upcoming \
  -H 'Authorization: Bearer {jwt_token}' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'
```

```ruby
RestClient::Request.new(
  :method => :get,
  :url => '{server_url}/api/v2/patients/{patient_id}/appointments/upcoming',
  :headers => {
    'Authorization' => 'Bearer {jwt_token}',
    'Content-type' => 'application/json',
    'Accept' => 'application/json'
  }
).execute
```

> The above command returns JSON structured like this:

```json
{
  "appointments":[
    {
      "id":1,
      "provider":{
        "id":36,
        "full_name": "Test Provider",
        "provider_type": "General Medical",
        "photo_file_name":"photo.jpg"
      },
      "start_date":"2018-01-17T19:18:14+00:00",
      "appointment_by":"video",
      "in_progress":false,
      "customer_call_in_number":"7866665555",
      "chief_complaint":"sore throat"
    }
  ]
}
```

### HTTP Request

To retrieve the list of a patient's upcoming appointments, make a request to:

`GET {server_url}/api/v2/patients/{patient_id}/appointments/upcoming`

### Headers

Parameter     | Default
--------------|------------------------
Authorization | Bearer {jwt_token}
Accept        | application/json
Content-type  | application/json

This request must include a valid User JWT token, please see our [documentation](#user-tokens).

### URL Parameters

The following parameters need to be included in the URL of the request:

Attribute  | Required | Description
-----------|----------|----------------------
patient_id | true     | MDLIVE ID for patient
