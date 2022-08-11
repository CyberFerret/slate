# Projects

## Get All Projects/Activities

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/projects'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/projects"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;

var client = new Client();
var endpoint = "https://api.hrpartner.io/projects";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this:

```json
[
	{
		"project": {
			"description": "Acme Inc - New Website",
			"cost_code": "100-100"
		},
		"activity_category": {
			"description": "Development",
			"cost_code": "00020"
		},
		"employee": {
			"code": "BLACK",
			"first_names": "Katrina",
			"last_name": "Black",
			"full_name": "Black, Katrina",
			"department": "Warehouse",
			"location": "Sydney Branch"
		},
		"transaction_date": "2021-06-14",
		"transaction_value": 2.5,
		"cost": 35.0,
		"charge": 35.0,
		"transaction_type": "timesheet",
		"currency": "Australia",
		"notes": "Acme Development"
	},
	{
		"project": {
			"description": "Reynolds - New Kitchen",
			"cost_code": "100-200"
		},
		"activity_category": {
			"description": "Drafting",
			"cost_code": ""
		},
		"employee": {
			"code": "BLACK",
			"first_names": "Katrina",
			"last_name": "Black",
			"full_name": "Black, Katrina",
			"department": "Warehouse",
			"location": "Sydney Branch"
		},
		"transaction_date": "2021-06-14",
		"transaction_value": 0.5,
		"cost": 13.0,
		"charge": 26.0,
		"transaction_type": "timesheet",
		"currency": "United States",
		"notes": "Reynolds Drafting"
	},
	{
		"project": {
			"description": "Reynolds - New Kitchen",
			"cost_code": "100-200"
		},
		"activity_category": {
			"description": "Meeting",
			"cost_code": ""
		},
		"employee": {
			"code": "BLACK",
			"first_names": "Katrina",
			"last_name": "Black",
			"full_name": "Black, Katrina",
			"department": "Warehouse",
			"location": "Sydney Branch"
		},
		"transaction_date": "2021-06-15",
		"transaction_value": 3.5,
		"cost": 50.0,
		"charge": 50.0,
		"transaction_type": "timesheet",
		"currency": "Australia",
		"notes": ""
	}
]
```

This endpoint retrieves all projects and activities that are currently in the system.

### HTTP Request

`GET https://api.hrpartner.io/projects`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
employee | text | Return only projects for employees with this employee code.
department | text | Specify one or more department names (separated by commas) to only show projects within that department.
location | text | Specify one or more location names (separated by commas) to only show projects within that location.
project | text | Specify the project name to only see activities that are against that particular project.
activity | text | Specify the activity name to see that activity across all projects.
expense_category | text | Specify the expense category code to only see projects/activities that are allocated to that expense category (only valid for expense project allocations)
currency | text | Specify the currency name to only see project costing amounts in that particular currency
transaction_date_from | date | Specify the starting date to see project costing entries for
transaction_date_to | date | Specify the ending date to see project costing entries for


### Examples

To get a list of all projects/activities for employee code ASMITH1:

`GET https://api.hrpartner.io/projects?employee=ASMITH1`

To get all activity against a project called "Smith Website Design" in June 2022:

`GET https://api.hrpartner.io/projects?project=Smith Website Design&transaction_date_from=2022-06-01&transaction_date_to=2022-06-30`

To get all "Drafting" activities across all projects, using the US Dollar currency:

`GET https://api.hrpartner.io/projects?activity=Drafting&currency=United States`


