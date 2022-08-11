# Leave Requests

## Get All Leave Requests

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/leave_requests'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/leave_requests"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;

var client = new Client();
var endpoint = "https://api.hrpartner.io/leave_requests";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this:

```json
[
	{
		"id": 146,
		"leave_request_type": "added",
		"absence_reason": "Time off in Lieu",
		"status": "submitted",
		"description": "Need 5.5 hours credit",
		"reason": "I banked up 5.5 hours leave yesterday by working overtime",
		"leave_start_date": "2022-07-22",
		"leave_end_date": "2022-07-22",
		"duration": 5.5,
		"units": "Hours",
		"notes": null,
		"employee": {
			"code": "MOREL",
			"first_names": "Landon",
			"last_name": "Moreno",
			"full_name": "Moreno, Landon",
			"department": "Floor Service"
		}
	},
	{
		"id": 144,
		"leave_request_type": "taken",
		"absence_reason": "Sick Leave",
		"status": "pending",
		"description": "Two days off",
		"reason": "",
		"leave_start_date": "2022-06-08",
		"leave_end_date": "2022-06-09",
		"duration": 2.0,
		"units": "Days",
		"notes": "Fine",
		"employee": {
			"code": "BUTTJ",
			"first_names": "James",
			"last_name": "Butterworth",
			"full_name": "Butterworth, James",
			"department": "Production"
		}
	},
	{
		"id": 142,
		"leave_request_type": "taken",
		"absence_reason": "Personal Leave",
		"status": "approved",
		"description": "Going hiking",
		"reason": "",
		"leave_start_date": "2022-04-27",
		"leave_end_date": "2022-04-29",
		"duration": 24.0,
		"units": "Hours",
		"notes": "OK",
		"employee": {
			"code": "BLENA",
			"first_names": "Arthur",
			"last_name": "Blenkinshop",
			"full_name": "Blenkinshop, Arthur",
			"department": "Sales"
		}
	},
	{
		"id": 143,
		"leave_request_type": "taken",
		"absence_reason": "Annual Leave",
		"status": "submitted",
		"description": "Need a 3 day break",
		"reason": "Going on a 3 day holiday trip with family.",
		"leave_start_date": "2022-04-21",
		"leave_end_date": "2022-04-25",
		"duration": 3.0,
		"units": "Days",
		"notes": null,
		"employee": {
			"code": "BLACK",
			"first_names": "Katrina",
			"last_name": "Black",
			"full_name": "Black, Katrina",
			"department": "Warehouse"
		}
	},
	{
		"id": 141,
		"leave_request_type": "taken",
		"absence_reason": "Annual Leave",
		"status": "approved",
		"description": "Boxer April Time",
		"reason": "",
		"leave_start_date": "2022-04-19",
		"leave_end_date": "2022-04-22",
		"duration": 4.0,
		"units": "Days",
		"notes": "Ok to go!",
		"employee": {
			"code": "BLACK",
			"first_names": "Katrina",
			"last_name": "Black",
			"full_name": "Black, Katrina",
			"department": "Warehouse"
		}
	}
]
```

This endpoint retrieves all employee leave requests that are currently in the system.

### HTTP Request

`GET https://api.hrpartner.io/leave_requests`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
employee | text | Return only leave requests for employees with this employee code.
department | text | Specify one or more department names (separated by commas) to only show leave requests within that department.
location | text | Specify one or more location names (separated by commas) to only show leave requests within that location.
leave_request_type | text | Specify whether you want to see leave requests for time off "taken" or TOIL/Flexi requests "added".
status | text | Specify the leave request status, which can be one of: submitted, pending, approved, rejected, revoked, withdrawn
absence_reason | text | Specify the leave policy name to isolate only leave requests against this particular policy/
description | text | Looks for a keyword within the leave request description.
reason | text | Looks for a keyword within the leave request reason text.
notes | text | Looks for a keyword within the leave request response notes made by any approvers.
leave_start_date_from | date | Specify the starting range for the leave start date.
leave_start_date_to | date | Specify the ending range for the leave start date.
leave_end_date_from | date | Specify the ending range for the leave end date.
leave_end_date_to | date | Specify the ending range for the leave end date.


### Examples

To get a list of all leave requests for employee code A12345:

`GET https://api.hrpartner.io/leave_requests?employee=A12345`

To get all requests for "Sick Leave" that started in July 2022:

`GET https://api.hrpartner.io/leave_requests?absence_reason=Sick Leave&leave_start_date_from=2022-07-01&leave_start_date_to=2022-07-31`

To get all requests for TOIL/Flexi additions in August 2022:

`GET https://api.hrpartner.io/leave_requests?leave_request_type=added&leave_start_date_from=2022-08-01&leave_start_date_to=2022-08-31`

To get all leave requests that contain the keyword "COVID" within the reason text:

`GET https://api.hrpartner.io/leave_requests?reason=COVID`


## Get A Specific Leave Request

```ruby
require 'rest-client'

header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}
endpoint = 'https://api.hrpartner.io/leave_request/'
leaverequestid = '144'

result = RestClient.get(endpoint + leaverequestid, header)

puts result
```

```shell
curl "https://api.hrpartner.io/leave_request/144"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;

var client = new Client();
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};
var endpoint = "https://api.hrpartner.io/leave_request/";
var leaverequestid = "144"

client.get(endpoint + leaverequestid, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this:

```json
{
	"id": 144,
	"leave_request_type": "taken",
	"absence_reason": "Personal Leave",
	"status": "pending",
	"description": "Two days off",
	"reason": "",
	"leave_start_date": "2022-06-08",
	"leave_end_date": "2022-06-09",
	"duration": 2.0,
	"units": "Hours",
	"notes": "Fine",
	"employee": {
		"code": "BUTTJ",
		"first_names": "James",
		"last_name": "Butterworth",
		"full_name": "Butterworth, James",
		"department": "Production",
		"location": "Perth Branch",
		"position": "Machinist",
		"employment_status": "Casual",
		"primary_email": "james@mailinator.com",
		"reports_to": {
			"code": "BLENA",
			"first_names": "Arthur",
			"last_name": "Blenkinshop",
			"full_name": "Blenkinshop, Arthur",
			"primary_email": "arthur@mailinator.com"
		}
	},
	"leave_approval_condition": "Local Sales Team",
	"leave_request_actions": [
		{
			"type": "user",
			"status": "none",
			"name": "Barbara McBain",
			"email": "barbara@mailinator.com",
			"actioned_at": null
		},
		{
			"type": "employee",
			"status": "approved",
			"name": "Blenkinshop, Arthur",
			"email": "arthur@mailinator.com",
			"actioned_at": "2022-06-07T04:15:57.000+00:00"
		},
		{
			"type": "user",
			"status": "none",
			"name": "John Snow",
			"email": "john@mailinator.com",
			"actioned_at": null
		}
	],
	"attachments": []
}
```

This endpoint retrieves a single reminder from the system using the **_Leave Request ID_**.

### HTTP Request

`GET https://api.hrpartner.io/leave_request/{leaverequestID}`

This call will return a single leave request based on the unique leave request ID from HR Partner.

<aside class="notice">Tip: You can use the <code>GET /leave_requests</code> call to get a list of all requests, then extract the <em>ID</em> field from the results to fetch individual requests.</aside>

The returned data contains a bit more information on the leave request, inlcluding any approver information, and any file attachments that may be linked to the original request.

