# Timesheets

## Get All Timesheets

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/timesheets'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/timesheets"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/timesheets";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this:

```json
[
	{
		"id": 1,
		"template": "Weekly Full Time Staff (Single)",
		"frequency": "weekly",
		"entry_method": "single",
		"rounding": "none",
		"round_to": 0,
		"closing_date": "2017-02-26",
		"max_lines": 3,
		"start_date": "2017-01-23",
		"end_date": "2017-01-29",
		"is_locked": "Yes",
		"status": "processed",
		"is_approved": "Yes",
		"is_exported": "No",
		"total_time": 27.25,
		"approving_user": "Devan Sabaratnam",
		"employee": {
			"code": "BLENA",
			"first_names": "Arthur",
			"last_name": "Blenkinshop",
			"full_name": "Arthur Blenkinshop",
			"department": "Sales",
			"location": "Main Office",
			"group": ""
		},
		"details": [
			{
				"entry_date": "2017-01-23",
				"start_time": "2017-01-23T08:30:00.000+00:00",
				"end_time": "2017-01-23T12:45:00.000+00:00",
				"break_duration": 0.5,
				"total_time": 3.75,
				"notes": "",
				"project": "",
				"cost_code": "",
				"activity": "",
				"cost": 0.0,
				"charge": 0.0,
				"currency": "Australia"
			},
			{
				"entry_date": "2017-01-24",
				"start_time": "2017-01-24T10:00:00.000+00:00",
				"end_time": "2017-01-24T17:00:00.000+00:00",
				"break_duration": 1.0,
				"total_time": 6.0,
				"notes": "",
				"project": "",
				"cost_code": "",
				"activity": "",
				"cost": 0.0,
				"charge": 0.0,
				"currency": "Australia"
			},
			{
				"entry_date": "2017-01-25",
				"start_time": "2017-01-25T23:00:00.000+00:00",
				"end_time": "2017-01-26T02:00:00.000+00:00",
				"break_duration": 0.25,
				"total_time": 2.75,
				"notes": "",
				"project": "",
				"cost_code": "",
				"activity": "",
				"cost": 0.0,
				"charge": 0.0,
				"currency": "Australia"
			},
			{
				"entry_date": "2017-01-26",
				"start_time": "2017-01-26T02:00:00.000+00:00",
				"end_time": "2017-01-26T17:00:00.000+00:00",
				"break_duration": 1.25,
				"total_time": 13.75,
				"notes": "",
				"project": "",
				"cost_code": "",
				"activity": "",
				"cost": 0.0,
				"charge": 0.0,
				"currency": "Australia"
			},
			{
				"entry_date": "2017-01-27",
				"start_time": "2017-01-27T13:00:00.000+00:00",
				"end_time": "2017-01-27T14:00:00.000+00:00",
				"break_duration": 0.0,
				"total_time": 1.0,
				"notes": "",
				"project": "",
				"cost_code": "",
				"activity": "",
				"cost": 0.0,
				"charge": 0.0,
				"currency": "Australia"
			}
		]
	},
	{
		"id": 2,
		"template": "Weekly Full Time Staff (Single)",
		"frequency": "weekly",
		"entry_method": "single",
		"rounding": "none",
		"round_to": 0,
		"closing_date": "2017-02-26",
		"max_lines": 3,
		"start_date": "2017-01-23",
		"end_date": "2017-01-29",
		"is_locked": "Yes",
		"status": "processed",
		"is_approved": "Yes",
		"is_exported": "No",
		"total_time": 13.0,
		"approving_user": "Devan Sabaratnam",
		"employee": {
			"code": "BURRS",
			"first_names": "Stacey",
			"last_name": "Burridge",
			"full_name": "Stacey Burridge",
			"department": "Warehouse",
			"location": "India",
			"group": ""
		},
		"details": [
			{
				"entry_date": "2017-01-23",
				"start_time": "2017-01-23T02:00:00.000+00:00",
				"end_time": "2017-01-23T05:00:00.000+00:00",
				"break_duration": 0.0,
				"total_time": 3.0,
				"notes": "",
				"project": "",
				"cost_code": "",
				"activity": "",
				"cost": 0.0,
				"charge": 0.0,
				"currency": "Australia"
			},
			{
				"entry_date": "2017-01-24",
				"start_time": "2017-01-24T02:00:00.000+00:00",
				"end_time": "2017-01-24T05:00:00.000+00:00",
				"break_duration": 0.0,
				"total_time": 3.0,
				"notes": "",
				"project": "",
				"cost_code": "",
				"activity": "",
				"cost": 0.0,
				"charge": 0.0,
				"currency": "Australia"
			},
			{
				"entry_date": "2017-01-25",
				"start_time": "2017-01-25T02:00:00.000+00:00",
				"end_time": "2017-01-25T05:00:00.000+00:00",
				"break_duration": 0.0,
				"total_time": 3.0,
				"notes": "",
				"project": "",
				"cost_code": "",
				"activity": "",
				"cost": 0.0,
				"charge": 0.0,
				"currency": "Australia"
			},
			{
				"entry_date": "2017-01-26",
				"start_time": "2017-01-26T03:00:00.000+00:00",
				"end_time": "2017-01-26T05:00:00.000+00:00",
				"break_duration": 0.0,
				"total_time": 2.0,
				"notes": "",
				"project": "",
				"cost_code": "",
				"activity": "",
				"cost": 0.0,
				"charge": 0.0,
				"currency": "Australia"
			},
			{
				"entry_date": "2017-01-27",
				"start_time": "2017-01-27T03:00:00.000+00:00",
				"end_time": "2017-01-27T05:00:00.000+00:00",
				"break_duration": 0.0,
				"total_time": 2.0,
				"notes": "",
				"project": "",
				"cost_code": "",
				"activity": "",
				"cost": 0.0,
				"charge": 0.0,
				"currency": "Australia"
			}
		]
	}
]
```

This endpoint retrieves all timesheets that are currently in the system.

Please note that the timesheets are grouped by Timesheet Template, then each sequence under that template, then the Employee, then the individual time entries for that employee.

### HTTP Request

`GET https://api.hrpartner.io/timesheets`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
employee | text | Return only timesheets for employee with this employee code.
department | text | Only return timesheets for employees with this department name.
location | text  | Only return timesheets for employees with this location name.
group | text | Only return timesheets for employees within this group/branch.
timesheet_name | text | Return only timesheets which have this timesheet template name.
timesheet_date_from | date | Return only timesheets with entries after this date (in `yyyy-mm-dd` format).
timesheet_date_to | date | Return only timesheets with entries before this date (in `yyyy-mm-dd` format). NOTE: Both from AND to dates must be specified.
sequence_start_date | date | Return only timesheets where the sequence starts on this date (in `yyyy-mm-dd` format).
sequence_end_date | date | Return only timesheets where the sequence ends on this date (in `yyyy-mm-dd` format).
timesheet status | text | Return only timesheets which have one of the following status in the header - `new`, `submitted`, `accepted`, `rejected` or `processed`.
project | text | Return only timesheets which have this project name attached to the entries.
activity | text | Return only timesheets which have this project activity name attached to the entries.
is_approved | true/false | Only return approved timesheets.
is_exported | true/false | Only return timesheet entries which are marked 'exported'.
is_locked | true/false | Allows you to specify timesheet sequences which are locked or unlocked.


<aside class="notice">Queries to obtain timesheet information can return LOTS of data, so please be sure to set valid parameters such as a date range or specific employees in order to minimise the information returned and to reduce any delays or timeouts.</aside>


### Examples

To get a list of all timesheets for employee code A12345:

`GET https://api.hrpartner.io/timesheets?employee=A12345`

To get all timesheets between 1st June and 30th June 2023:

`GET https://api.hrpartner.io/timesheets?timesheet_date_from=2023-06-01&timesheet_date_to=2023-06-30`

To get all timesheets for the "Main Office" location, that have been approved but are still unlocked:

`GET https://api.hrpartner.io/timesheets?location=Main Office&status=approved&is_locked=false`

To get all timesheets for the project "Office Rebuild", for all timesheet sequences starting on 1st July 2023:

`GET https://api.hrpartner.io/timesheets?project=Office Rebuild&sequence_start_date=2023-07-01`


## Add A Timesheet/Timeclock Entry

```ruby
require 'rest-client'

# Update Arthur's current (open) timesheet with an entry for 3 hours work on Project Acme
endpoint = 'https://api.hrpartner.io/employee/'
payload = {
  "employee_code": "BLENA",
  "start_time": "2023-08-20 08:15",
  "end_time": "2023-08-20 12:45",
  "project_name": "ACME Holdings",
  "notes": "Met with clients"
}

result = RestClient.execute(
	:method => :post,
  	:url => endpoint,
  	:payload => payload,
  	:headers => {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d',	content_type: "multipart/form-data"}
)

puts result
```

```shell
curl -v
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
  -F "employee_code=BLENA"
  -F "start_time=2023-08-20 08:15"
  -F "end_time=2023-08-20 12:45"
  -F "project_name=ACME Holdings"
  -F "notes=Met with clients"
  https://api.hrpartner.io/timesheet
```

```javascript
var Client = require('node-rest-client').Client;

var client = new Client();

// Update Arthur's record with tax number, update custom fields with new salary and work times, add contractor tag, change mobile number and add new email
var payload = {
  "employee_code": "BLENA",
  "start_time": "2023-08-20 08:15",
  "end_time": "2023-08-20 12:45",
  "project_name": "ACME Holdings",
  "notes": "Met with clients"
}

var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}, formData: payload};
var endpoint = "https://api.hrpartner.io/timesheet";

client.post(endpoint, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this upon successful save to the timesheet entry:

```json
{
	"message": "Timesheet entry was successfully created."
}
```

If there is an error, then the specific error will be returned as a JSON message.


### HTTP Request

`POST https://api.hrpartner.io/timeclock`

A successful POST will return a single JSON message notifying you of a successful save.  Otherwise you will see an error message explaining why the timesheet entry was not saved.

### POST Data

The timesheet endpoint can only accept `multipart/form-data` fields (similar to POSTing an HTML form).  This is to ensure maximum compatibility with various systems that integrate with HR Partner.

Parameter | Type | Description
--------- | ---- | -----------
employee_code<sup>*</sup> | text | The employee code (Please note that this is different from other endpoints that just take `employee` as the parameter).
employee_email<sup>*</sup> | text | The employee email (as an alternative to the code if you don't have it).  Either the code or the email MUST be specified.
start_time<sup>*</sup> | datetime | The starting time, in local time ISO-8601 format `yyyy-mm-dd hh:mm`.
end_time<sup>*</sup> | datetime | The ending time, in local time ISO-8601 format `yyyy-mm-dd hh:mm`.
duration | number | You can optionally specify the duration.  If not specified, it will be calculated from the start and end time.  If you specify a duration _less_ than the calculated duration, then the difference will be assumed to be Break Time.
break | number | You can specify the break time which will be deducted from the duration.  If not specified, the difference between the calculated duration and the duration passed to the API will be recorded as the break time.
notes | text | Notes to be recorded against the entry.
project_name | text | The name of an existing Project to record the time against.
activity_name | text | The name of an existing project Activity to record the time against.

_<sup>*</sup> - Mandatory (required) field_

<aside class="notice">Please note that you must specify either the `employee_code` or `employee_email` in the data so that we know which employee to apply the timesheet entry to.</aside>

Important considerations:

* You must have the timeclock module enabled in HR Partner to accept time entries via the API
* The employee's timesheet template must have timeclock entries enabled
* Times can only be POSTed against OPEN timesheet sequences.  Any closed sequences will result in rejected times
* Times must be in the employee's local timezone only, and you have to specify full dates and times in ISO-8601 format, which is `yyyy-mm-dd hh:mm`
* You must specify a starting AND ending date/time
* The `duration` is an optional field and can be omitted, but if you specify a duration that is _less_ than the calculated times, then the difference will be considered the break time.
* The `break` is an optional field and can be omitted, and if you don't specify a break time, then the difference between the calculated duration from the start/end times minus the `duration` specified will be used to calculate the break time.

