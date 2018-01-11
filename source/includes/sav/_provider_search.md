## Searching for Providers

```shell
curl -X POST {server_url}/api/v1/patients/{patient_id}/providers/search
-H "Content-type: application/json"
-H "Authorization: Bearer 34a2sample-user-token"
-d '{ "search": {
         "state_abbrev": "FL",
       }
    }'
```

```ruby
RestClient::Request.new(
  method: :post,
  url: "#{server_url}/api/v1/patients/#{patient_id}/providers/search",
  headers: {
    "Content-type" => "application/json",
    "Authorization" => "Bearer 34a2sample-user-token"
  },
  payload: {
    search_params: {state_abbrev: "FL"}
  }
).execute
```
> The above command returns JSON structured like this:

```json

{
  "providers": [
    {
      "id": 542127369,
      "fullname": "Dr. Keylime Pie",
      "gender": "Female",
      "photo_url": null,
      "specialty": "General Practice",
      "group_name": null,
      "is_mental_health_provider": false,
      "is_visit_now_available": false,
      "patient_can_request_appointment": true,
      "status": "Available",
      "next_appt_available_date": "2017-11-09T13:45:00-05:00",
      "availability_type": null
    },
    {
      "id": 542114314,
      "fullname": "Dr. Test Amalie",
      "gender": "Male",
      "photo_url": null,
      "specialty": "General Practice",
      "group_name": null,
      "is_mental_health_provider": false,
      "is_visit_now_available": false,
      "patient_can_request_appointment": true,
      "status": "Available",
      "next_appt_available_date": "2017-11-09T13:45:00-05:00",
      "availability_type": null
    },
    {
      "id": 542117784,
      "fullname": "Dr. Andy Available",
      "gender": "Male",
      "photo_url": null,
      "specialty": "General Practice",
      "group_name": null,
      "is_mental_health_provider": false,
      "is_visit_now_available": false,
      "patient_can_request_appointment": true,
      "status": "Available",
      "next_appt_available_date": "2017-11-09T13:45:00-05:00",
      "availability_type": null
    }
  ],
  "video_waiting_room_open": true,
  "refine_search_options": {
    "default_provider_types": [
      {
        "id": 3,
        "name": "Family Physician",
        "had_consult_24_hr": false
      },
      {
        "id": 5,
        "name": "Therapist",
        "had_consult_24_hr": false
      },
      {
        "id": 6,
        "name": "Psychiatrist",
        "had_consult_24_hr": false
      },
      {
        "id": 12,
        "name": "Dermatologist",
        "had_consult_24_hr": false
      }
    ],
    "availability_type": [
      "phone",
      "video"
    ]
  }
}

```

The first step in scheduling a visit is searching for available providers for a patient.

This request must include a valid User JWT token, please see our [documentation](#user-tokens)

### HTTP Request

`POST {server_url}/api/v1/patients/{patient_id}/providers/search`

### Header Parameter

Parameter     | Default          | Description
---------     | -------          | -------
Content-type  | application/json | Expected content type, currently only JSON is supported
Authorization | Bearer {TOKEN}   | Auth Token, should be the string "Bearer {TOKEN}" where {Token} is the token received from the patient auth endpoint

### URL Parameter
Attribute | Required | Description
--------- | ------- | -----------
patient_id | true| MDLIVE ID for patient

### Request Body

Attribute     |                | Required  | Description
---------     |---------       | --------  | -----------
search_params |                | true      | Hash with specific search filters
              | state_abbrev   | true      | 2 Letter state abbreviated, from the states list
              | availability_type| false   | Can be either 'phone' or 'video', use to specify the preferred type of appointment for the patient
              | gender         | false     | Preferred Provider gender (Male or Female string)
              | provider_type  | false     | Provider Type ID, from the provider types list (or the endpoint response)
              | specific_date  | false     | Date in YYYY-mm-dd format
              | speciality_id  | false     | Provider Specialty for filtering, obtained from this endpoint response
