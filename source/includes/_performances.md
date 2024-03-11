# Performance Management

## Get All Performance Reviews

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/performances'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/performances"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;

var client = new Client();
var endpoint = "https://api.hrpartner.io/performances";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 103600,
    "status": "Pending",
    "template": "6 Monthly Review",
    "responses": [],
    "assigned_at": "2022-04-04T01:53:01.000+00:00",
    "review_date": "2022-04-04",
    "completed_at": null,
    "employee": {
      "code": "COLLG",
      "first_names": "Gracie",
      "last_name": "Collins",
      "full_name": "Gracie Collins",
      "department": "Flight Operations"
    }
  },
  {
    "id": 103615,
    "status": "Pending",
    "template": "6 Monthly Review",
    "responses": [],
    "assigned_at": "2022-04-05T11:53:22.000+00:00",
    "review_date": "2022-04-21",
    "completed_at": null,
    "employee": {
      "code": "CRANT",
      "first_names": "Troy",
      "last_name": "Crandon",
      "full_name": "Troy Crandon",
      "department": "Administration"
    }
  },
  {
    "id": 103622,
    "status": "Pending",
    "template": "6 Monthly Review",
    "responses": [],
    "assigned_at": "2022-04-06T10:58:32.000+00:00",
    "review_date": "2022-04-28",
    "completed_at": null,
    "employee": {
      "code": "DARBS1",
      "first_names": "Susan",
      "last_name": "Darby",
      "full_name": "Susan Darby",
      "department": "Administration"
    }
  },
  {
    "id": 103623,
    "status": "Planned",
    "template": "Annual Performance Review",
    "responses": [],
    "assigned_at": "2022-04-07T03:42:32.000+00:00",
    "review_date": "2023-04-06",
    "completed_at": null,
    "employee": {
      "code": "BOGLT",
      "first_names": "Tucker",
      "last_name": "Bogle",
      "full_name": "Tucker Bogle",
      "department": "Engineering"
    }
  }
]
```

This endpoint retrieves all performance management reviews that are currently in the system.

### HTTP Request

`GET https://api.hrpartner.io/performances`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
employee | text | Return only reviews for employees with this employee code.
department | text | Specify one or more department names (separated by commas) to only show reviews within that department.
location | text | Specify one or more location names (separated by commas) to only show reviews within that location.
position | text | Specify one or more position names (separated by commas) to only show reviews where the employee has that position.
employment_status | text | Specify one or more employment status names (separated by commas) to only show reviews for employees with that employment status.
review_status | text | Can be ONE of `planned`, `pending`, `complete` or `cancelled` or leave blank for all.
assigned_date_from | date | Specify the starting date that the reviews were assigned out (yyyy-mm-dd).
assigned_date_to | date | Specify the ending date that the reviews were assigned out (yyyy-mm-dd).
review_date_from | date | Specify the starting date that the reviews were due at (yyyy-mm-dd).
review_date_to | date | Specify the ending date that the reviews were due at (yyyy-mm-dd).
completed_date_from | date | Specify the starting date that the reviews were completed (yyyy-mm-dd).
completed_date_to | date | Specify the ending date that the reviews were completed (yyyy-mm-dd).
form_data | text | Can be any of `employee`, `manager`, `peer` or `user` to retrieve the individual form statuses, or leave blank for all.
include_answers | true/false | Specify `true` if you wish to see all the questions/answers for the above forms.

Please note that the form data and questions/answers are NOT included in the JSON response by default unless the flags above are specified to return that information.  Be aware that including this information can significantly increase the response time of your queries, so be sure to specify other filters to reduce the number of reviews being returned.


### Examples

To get a list of all performance reviews for employees in the Location "London":

`GET https://api.hrpartner.io/performances?location=London`

To get all pending reviews that were assigned out in April 2024:

`GET https://api.hrpartner.io/performances?review_status=pending&assigned_date_from=2024-04-01&assigned_date_to=2024-04-31`

To get all reviews due in December 2024, and see the employee and manager form questions and answers:

`GET https://api.hrpartner.io/performances?review_date_from=2024-12-01&review_date_to=2024-12-31&form_data=employee,manager&include_answers=true`


The below example shows the response with the `employee` and `manager` **form_data** specified, and with the **include_answers** parameter set to `true`

```
[
  {
    "id": 103600,
    "status": "Pending",
    "template": "6 Monthly Review",
    "responses": [
      {
        "type": "Employee",
        "reviewer": "Gracie Collins",
        "status": "Complete",
        "form": "Employee Self Review",
        "answers": [
          {
            "question": "I feel clear about my role and responsibilities:",
            "type": "radio-group",
            "answer": "Yes, No further information required"
          },
          {
            "question": "I feel like I'm making an important contribution in my role",
            "type": "radio-group",
            "answer": "Significant Contribution"
          },
          {
            "question": "I feel a sense of connection and camaraderie with my team",
            "type": "radio-group",
            "answer": "Superficial Connection Only"
          },
          {
            "question": "What are you most proud of achieving since your last review?",
            "type": "textarea",
            "answer": "I think I did quite well with the new CRM system that was rolled out in January. I enjoyed teaching others how to use this new tool.\r\nMy customer satisfaction ratings for support tickets have also improved since last time."
          },
          {
            "question": "What areas have been the most challenging for you?",
            "type": "textarea",
            "answer": "I struggle with technical support queries and feel I don't have enough knowledge to answer these properly."
          },
          {
            "question": "What would you like to focus on for the next period?",
            "type": "textarea",
            "answer": "I'd like to stay involved in the continued rollout of the CRM and put my hand up for any similar projects.\r\nI'd also like to spend some time increasing my technical knowledge."
          },
          {
            "question": "How can management best support you in achieving this?",
            "type": "textarea",
            "answer": "Time and guidance as to how to increase technical knowledge."
          },
          {
            "question": "How would you rate your overall satisfaction and motivation towards your role at the moment?",
            "type": "starRating",
            "answer": "7"
          },
          {
            "question": "What would help to improve that rating?",
            "type": "textarea",
            "answer": "Feeling more competent. Plus, "
          },
          {
            "question": "Date of Completion",
            "type": "date",
            "answer": "2022-04-03"
          }
        ]
      },
      {
        "type": "Manager",
        "reviewer": "Troy Crandon",
        "status": "Complete",
        "form": "Manager Review",
        "answers": [
          {
            "question": "How often does this employee embrace and live the company values?",
            "type": "radio-group",
            "answer": "Quite Often"
          },
          {
            "question": "What are this employee's most significant achievements since their last review?",
            "type": "textarea",
            "answer": "Gracie has been instrumental in the rollout of our new CRM system. She has managed to achieve this while keeping up with support tickets and achieving a very high customer satisfaction area."
          },
          {
            "question": "What areas do they have the most opportunity to improve?",
            "type": "textarea",
            "answer": "Gracie seems to lack some confidence with trouble-shooting technical problems."
          },
          {
            "question": "What areas would you like them to focus on for the next period?",
            "type": "textarea",
            "answer": "Would recommend she takes on another project to grow further with project management. We are looking for a new chat system and I'd like Gracie to lead this."
          },
          {
            "question": "How do you plan to support the employee in achieving this?",
            "type": "textarea",
            "answer": "Weekly checkins to mentor and troubleshoot problems as they arise."
          },
          {
            "question": "Overall, how did this employee perform since their last review?",
            "type": "starRating",
            "answer": "9.5"
          },
          {
            "question": "Date of Completion",
            "type": "date",
            "answer": "2022-04-04"
          }
        ]
      }
    ],
    "assigned_at": "2022-04-04T01:53:01.000+00:00",
    "review_date": "2022-04-04",
    "completed_at": null,
    "employee": {
      "code": "COLLG",
      "first_names": "Gracie",
      "last_name": "Collins",
      "full_name": "Gracie Collins",
      "department": "Flight Operations"
    }
  }
]
```
