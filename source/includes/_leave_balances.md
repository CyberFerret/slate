# Leave Balances

## Get All Leave Balances

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/leave_balances'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/leave_balances"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;

var client = new Client();
var endpoint = "https://api.hrpartner.io/leave_balances";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this:

```json
[
	{
		"absence_reason": "Annual Leave",
		"is_external": false,
		"entitlement": 20.0,
		"balance": 7.5,
		"carryover": 0.0,
		"units": "Days",
		"auto_accrual": true,
		"last_accrual_done_at": "2022-11-08",
		"reset_carry_over_at": null,
		"last_reset_at": "2022-01-01",
		"next_reset_at": "2023-01-01",
		"periods_since_last_reset": 11.0,
		"periods_until_next_reset": 1.0,
		"periodic_increment": 1.66666667,
		"employee": {
			"code": "JONESM",
			"first_names": "Mike",
			"last_name": "Jones",
			"full_name": "Jones, Mike",
			"department": "Sales"
		}
	},
	{
		"absence_reason": "Sick Leave",
		"is_external": false,
		"entitlement": 10.0,
		"balance": 8.0,
		"carryover": 0.0,
		"units": "Days",
		"auto_accrual": true,
		"last_accrual_done_at": "2022-11-08",
		"reset_carry_over_at": null,
		"last_reset_at": null,
		"next_reset_at": null,
		"periods_since_last_reset": 11.0,
		"periods_until_next_reset": 1.0,
		"periodic_increment": 0.83333333,
		"employee": {
			"code": "JONESM",
			"first_names": "Mike",
			"last_name": "Jones",
			"full_name": "Jones, Mike",
			"department": "Sales"
		}
	},
	{
		"absence_reason": "Annual Leave",
		"is_external": false,
		"entitlement": 24.0,
		"balance": 19.0,
		"carryover": 3.0,
		"units": "Days",
		"auto_accrual": true,
		"last_accrual_done_at": "2022-11-08",
		"reset_carry_over_at": "2022-12-31",
		"last_reset_at": "2022-01-01",
		"next_reset_at": "2023-01-01",
		"periods_since_last_reset": 11.0,
		"periods_until_next_reset": 1.0,
		"periodic_increment": 2.0,
		"employee": {
			"code": "SMITHJ",
			"first_names": "Jane",
			"last_name": "Smith",
			"full_name": "Smith, Jane",
			"department": "Finance"
		}
	},
	{
		"absence_reason": "Sick Leave",
		"is_external": false,
		"entitlement": 10.0,
		"balance": 6.5,
		"carryover": 0.0,
		"units": "Days",
		"auto_accrual": true,
		"last_accrual_done_at": "2022-11-08",
		"reset_carry_over_at": null,
		"last_reset_at": null,
		"next_reset_at": null,
		"periods_since_last_reset": 11.0,
		"periods_until_next_reset": 1.0,
		"periodic_increment": 0.83333333,
		"employee": {
			"code": "SMITHJ",
			"first_names": "Jane",
			"last_name": "Smith",
			"full_name": "Smith, Jane",
			"department": "Finance"
		}
	}
]
```

This endpoint retrieves all employee leave balances that are currently in the system.

### HTTP Request

`GET https://api.hrpartner.io/leave_balances`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
absence_reason | text | Specify the leave policy name to isolate only leave balances against this particular policy.
employee | text | Return only leave balances for employees with this employee code.
department | text | Specify one or more department names (separated by commas) to only show leave balances within that department.
location | text | Specify one or more location names (separated by commas) to only show leave balances within that location.
employment_status | text |  Specify one or more employment statuses (separated by commas) to only show leave balances for those positions.
position | text | Specify one or more position names (separated by commas) to only show leave balances for those positions.
is_active | true/false | Specify whether to include active employees in returned data. (default: true)
is_terminated | true/false | Specify whether to include terminated employees in returned data. (default: true)


### Examples

To get a list of all leave balances for employee code A12345:

`GET https://api.hrpartner.io/leave_balances?employee=A12345`

To get all balances for "Annual Leave":

`GET https://api.hrpartner.io/leave_balances?absence_reason=Annual Leave`

To get all balances for non-terminated employees in the Finance department:

`GET https://api.hrpartner.io/leave_balances?department=Finance&is_terminated=false`


<aside class="notice">NOTE: The fetching of leave balances can take a long time to process, due to the complicated calculations required in the returned data.  Please try to filter your results to return the smallest data set possible, and try to refrain from making too many calls to this endpoint in a short space of time to preserve our server performance capacity.</aside>

### Returned Data

The below table gives some extra information on the data returned from this call, which may not be self explanatory.

Field | Type | Description
----- | ---- | -----------
absence_reason | text | The name of the leave policy that this balance applies to.
is_external | true/false | Denotes whether this policy has come from an external payroll system (i.e not maintained within HR Partner).
entitlement | number | The annual allowance or entitlement that the employee is allocated for this policy.
balance | number | The employee's current balance for the policy as at the time of running the query.
carryover | number | The amount of carried forward balance when the last reset happened.
units | text | The units that the above numbers represent (Days or Hours).
auto_accrual | true/false | Whether the employee has auto accruals turned on for this policy.
last_accrual_done_at | date | The date that the last accrual calculation was done in HR Partner.
reset_carryover_at | date | The date that any carried forward balance will be reset.
last_reset_at | date | The date this leave policy was last reset.
next_reset_at | date | The date that this leave policy will next reset.
periods_since_last_reset | number | The number of calculation periods since the last reset was done (depending on whether the policy is set for days/weeks/quarters/months for the calculation period).
priods_until_next_reset | number | As above, but shows the periods until the next reset is due.
periodic_increment | number | The number of Days/Hours to increment each day/week/month/quarter as per the leave policy setup.

