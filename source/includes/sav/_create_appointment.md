## Creating the appointment
```shell
curl -X POST {server_url}/api/v2/patients/{patient_id}/appointments
-H "Content-type: application/json" \
-H "Authorization: Bearer 34a2sample-api-token"
-d '{
      "appointment": {
        "provider_id": 4,
        "provider_type_id": 3,
        "state_abbrev": "FL",
        "customer_call_in_number": "5555555555",
        "start_time": 1516225743,
        "survey_answer": "Emergency Room",
        "appointment_method": "phone",
        "chief_complaint": "Throat Pain",
        "concept_id": 64,
        "agrees_to_informed_consent": true,
        "agrees_to_privacy_agreement": true,
        "consent_user_initials": "TM",
        "pcp_questions": [
          {
            "question": "primary_care_physician",
            "answer": true
          },
          {
            "question": "pcp_correct_information",
            "answer": true
          },
          {
            "question": "pcp_visit_information",
            "answer": true
          },
          {
             "question": "pcp_assistance_question",
             "answer": false
          }
        ]
      }
    }'
```
```ruby
RestClient::Request.new(
  :method => :post,
  :url => "{server_url}/api/v2/patients/{patient_id}/appointments",
  :headers => {
    "Content-type" => "application/json",
    "Authorization" => "Bearer 34a2sample-api-token"
  },
  :payload => {
      "appointment"=> {
          "provider_id"=> 4,
          "provider_type_id"=> 3,
          "state_abbrev"=> "GA",
          "customer_call_in_number"=> "5555555555",
          "start_time"=> 1516225743,
          "survey_answer"=> "Emergency Room",
          "appointment_method"=> "phone",
          "chief_complaint"=> "Throat Pain",
          "concept_id"=> 64,
          "agrees_to_informed_consent"=> true,
          "agrees_to_privacy_agreement"=> true,
          "consent_user_initials"=> "TM",
          "pcp_questions"=> [
            {
              "question"=> "primary_care_physician",
              "answer"=> true
            },
            {
              "question"=> "pcp_correct_information",
              "answer"=> true
            },
            {
              "question"=> "pcp_visit_information",
              "answer"=> true
            },
            {
               "question"=> "pcp_assistance_question",
               "answer"=> false
            }
          ]
        }
      }
).execute
```
> The above command returns JSON structured like this:

```json
{
  "appointment": {
    "id": 71,
    "user_id": 3,
    "phys_availability_id": 112,
    "physicianId": 4,
    "appointment_status_id": 1,
    "created_at": "2018-01-19T10:54:38.988-05:00",
    "updated_at": "2018-01-19T10:54:38.997-05:00",
    "customer_on_call_queue_id": null,
    "appointment_method_id": 2,
    "customer_call_in_number": "5555555555",
    "chief_complaint": "Throat Pain",
    "consultation_token": null,
    "state_id": 11,
    "cs_support_cases_id": null,
    "cust_appointment_type": "Diagnostic",
    "concept_id": 64,
    "chief_complaint_comments": null,
    "provider_chief_complaint": null,
    "order_id": 12,
    "video_backend": null,
    "physician_type_id": 3,
    "id_from_emr": null,
    "affiliation_id": 96,
    "start_time": "2018-01-19T14:50:35.000-05:00"
  }
}
```


The final step to create an appointment is to call the endpoint, passing in all the determined preferred values for the appointment.

### HTTP Request

`POST {server}/api/v2/patients/{patient_id}/appointments`

This request must include a valid User JWT token, please see our [documentation](#user-tokens)

### Header Parameter

Parameter | Default
--------- | -------
Content-type | application/json
Authorization| Bearer {jwttoken}

The following parameters are required when creating an appointment.

### URL Parameter
Attribute | Required | Description
--------- | ------- | -----------
patient_id | true| MDLIVE ID for patient

### Request Body Parameters

Attribute | Required | Description
--------- | ------- | -----------
appointment| true | parent attribute for the appointment
↳&nbsp;provider_type_id | true | Requested doctor type for appointment, found in [provider types list](#provider-types) (or the endpoint response)
↳&nbsp;state_abbrev | true | Requested U.S. [state](#states) for the appointment
↳&nbsp;survey_answer | true | Answer to survey question
↳&nbsp;customer_call_in_number | true | Preferred phone number to contact the patient
↳&nbsp;appointment_method | true | Requested type of appointment for the patient, should be 'video' or 'phone'
↳&nbsp;start_time | true | Requested time for appointment as integer  seconds since Epoch
↳&nbsp;chief_complaint | true | Reason for the appointment
↳&nbsp;provider_id | false | Id of the requested [provider](#getting-a-provider-39-s-profile). Needed only when the patient would like to schedule a visit with a specific provider.
↳&nbsp;chief_complaint_comments | false | Any additional description of the reason the patient is making the appointment
↳&nbsp;concept_id | false | Id returned from auto-complete search of [Clinical Concepts](#clinical-concepts-search) for the patient's chief complaint
↳&nbsp;file_id | false | Id of the document to attach to the appointment.
↳&nbsp;promocode | false | Promocode to apply to the cost of the appointment
↳&nbsp;agrees_to_informed_consent | true | Patient's answer to if they agree to the terms of MDLIVE Medical Group's Informed Consent
↳&nbsp;agrees_to_privacy_agreement | true | Patient's answer to if they agree to the terms MDLIVE Medical Group's Privacy Policy
↳&nbsp;consent_user_initials | true | Initials entered by patient to indicate they have answered the agreement questions
↳&nbsp;pcp_questions| false | parent attribute for array of Primary Care Physician questions
&nbsp;&nbsp;&nbsp;&nbsp;↳&nbsp;question| false | Name for [PCP question](#primary-care-physician-questions-retrieve-questions)
&nbsp;&nbsp;&nbsp;&nbsp;↳&nbsp;answer | false | True or False answer to the Primary Care Physician question
