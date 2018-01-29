## Alternate Visit Options - List

The options to be chosen by the patient in case MDLIVE was not available for the appointment.

```shell
curl -X GET {server_url}/api/v1/support/alternate_visit_options \
  -H 'Authorization: Bearer {jwt_token}' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'
```

```ruby
RestClient::Request.new(
  :method => :get,
  :url => '{server_url}/api/v1/support/alternate_visit_options',
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
  "alternate_visit_options": [
    "1. Emergency Room",
    "2. Urgent Care",
    "3. Primary Care Physician",
    "4. Delay Seeking Care",
    "5. Other"
  ]
}
```


### HTTP Request

To retrieve the list of alternate visit options, make a request to:

`GET {server_url}/api/v1/support/alternate_visit_options`


### Headers

Parameter     | Default
--------------|------------------------
Authorization | Bearer {jwt_token}
Content-type  | application/json
Accept        | application/json

This request must include a valid JWT token, please see our [documentation](#api-tokens).
