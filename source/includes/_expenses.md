# Expenses

## Get All Expense Claims

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/expenses&report_type=detailed'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/expenses&report_type=detailed"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;

var client = new Client();
var endpoint = "https://api.hrpartner.io/expenses&report_type=detailed";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this (if a <strong>report_type</strong> of 'detailed' or 'summary' is selected):

```json
[
	{
		"id": 2,
		"description": "Client meeting with Anderson",
		"comment": "Meeting across town for the Anderson housing project.",
		"status": "approved",
		"is_paid": true,
		"expense_date": "2022-11-19",
		"submitted_date": "2022-11-25",
		"approved_date": "2022-11-25",
		"reimbursement_required": "Yes",
		"total_amount": 43.20,
		"total_tax_amount": 0.0,
		"reimbursement_amount": 43.20,
		"currency": "Australia",
		"action_user": "Joe Smith",
		"data_type": "detailed",
		"employee": {
			"code": "BLACK",
			"first_names": "Katrina",
			"last_name": "Black",
			"full_name": "Black, Katrina",
			"department": "Warehouse",
			"location": "Sydney Branch"
		},
		"lines": [
			{
				"category": "Meals",
				"details": "Cafe lunch",
				"amount": 21.50,
				"tax_amount": 0.0,
				"project": "Anderson Project",
				"cost_code": "030-23",
				"cost": 0.0,
				"charge": 0.0,
				"currency": "Australia"
			},
			{
				"category": "Fuel",
				"details": "Filled up car",
				"amount": 21.70,
				"tax_amount": 0.0,
				"project": "Anderson Project",
				"cost_code": "031-22",
				"cost": 0.0,
				"charge": 0.0,
				"currency": "Australia"
			}
		]
	},
	{
		"id": 3,
		"description": "Overnight trip to Sydney",
		"comment": "This is my trip to Sydney for the conference.",
		"status": "approved",
		"is_paid": true,
		"expense_date": "2022-11-19",
		"submitted_date": "2022-11-25",
		"approved_date": null,
		"reimbursement_required": "Yes",
		"total_amount": 1106.9,
		"total_tax_amount": 0.0,
		"reimbursement_amount": 0.0,
		"currency": "Australia",
		"action_user": "Mary Stuart",
		"data_type": "detailed",
		"employee": {
			"code": "BLACK",
			"first_names": "Katrina",
			"last_name": "Black",
			"full_name": "Black, Katrina",
			"department": "Warehouse",
			"location": "Sydney Branch"
		},
		"attachments": [
			{
				"description": "expense_claim1.png",
				"url": "975C205D6F2E2CE7A8AE93441F038023/expenses/u3tyyAh0OUtUbnPni41lXA/expense_claim1.png",
				"size": 9624
			},
			{
				"description": "Recruitment-Best-Practices-833x554.png",
				"url": "975C205D6F2E2CE7A8AE93441F038023/expenses/4U5UCo6hNjjp44AIgw8Aig/qantas_invoice.png",
				"size": 412644
			}
		],
		"lines": [
			{
				"category": "Flights",
				"details": "Qantas QF677",
				"amount": 679.2,
				"tax_amount": 0.0,
				"project": "",
				"cost_code": "031-74",
				"cost": 0.0,
				"charge": 0.0,
				"currency": "Australia"
			},
			{
				"category": "Car Hire",
				"details": "Hertz Corolla",
				"amount": 67.1,
				"tax_amount": 0.0,
				"project": "",
				"cost_code": "031-22",
				"cost": 0.0,
				"charge": 0.0,
				"currency": "Australia"
			},
			{
				"category": "Hotels",
				"details": "Radison (1 night)",
				"amount": 360.6,
				"tax_amount": 0.0,
				"project": "",
				"cost_code": "030-45",
				"cost": 0.0,
				"charge": 0.0,
				"currency": "Australia"
			}
		]
	}
]
```

> The above command returns JSON structured like this (if a <strong>report_type</strong> of 'transaction' is selected):

```json
[
	{
		"id": 26,
		"category": "Meals",
		"details": "Meal vouchers",
		"amount": 250.0,
		"tax_amount": 0.0,
		"description": "Melbourne Training Session",
		"status": "submitted",
		"expense_date": "2022-11-07",
		"submitted_date": "2022-11-25",
		"approved_date": "2022-12-16",
		"employee_code": "BLACK",
		"employee_name": "Black, Katrina",
		"project": "",
		"cost_code": "030-23",
		"cost": 0.0,
		"charge": 0.0,
		"currency": "Australia",
		"data_type": "transaction"
	},
	{
		"id": 27,
		"category": "Car Hire",
		"details": "Travan Hire",
		"amount": 145.6,
		"tax_amount": 0.0,
		"description": "Melbourne Training Session",
		"status": "submitted",
		"expense_date": "2022-11-07",
		"submitted_date": "2022-11-25",
		"approved_date": "2022-12-16",
		"employee_code": "BLACK",
		"employee_name": "Black, Katrina",
		"project": "",
		"cost_code": "031-22",
		"cost": 0.0,
		"charge": 0.0,
		"currency": "Australia",
		"data_type": "transaction"
	},
	{
		"id": 28,
		"category": "Hotels",
		"details": "Yates Motel",
		"amount": 325.9,
		"tax_amount": 0.0,
		"description": "Melbourne Training Session",
		"status": "submitted",
		"expense_date": "2022-11-07",
		"submitted_date": "2022-11-25",
		"approved_date": "2022-12-16",
		"employee_code": "BLACK",
		"employee_name": "Black, Katrina",
		"project": "",
		"cost_code": "030-45",
		"cost": 0.0,
		"charge": 0.0,
		"currency": "Australia",
		"data_type": "transaction"
	},
	{
		"id": 29,
		"category": "Meals",
		"details": "Seminar Dinner",
		"amount": 77.1,
		"tax_amount": 0.0,
		"description": "Melbourne Training Session",
		"status": "submitted",
		"expense_date": "2022-11-07",
		"submitted_date": "2022-11-25",
		"approved_date": "2022-11-29",
		"employee_code": "BLACK",
		"employee_name": "Black, Katrina",
		"project": "",
		"cost_code": "030-23",
		"cost": 0.0,
		"charge": 0.0,
		"currency": "Australia",
		"data_type": "transaction"
	}
]
```

This endpoint retrieves all expense claims that are currently in the system.

### HTTP Request

`GET https://api.hrpartner.io/expenses?report_type={expenseReportType}`

<aside class="notice">NOTE: This endpoint <strong>requires</strong> the <em>expenseReportType</em> to be specified in order to return meaningful data (seel below).</aside>

### Expense Report Type Parameter

The _expenseReportType_ parameter must be one of the following:

detailed | A list of expense claim headers along with the associated individual expense lines and attachments.
summary | A list of only the expense claim headers (without individual expense lines or attachments).
transaction | A list of expense detail lines only.

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
report_type | text | MANDATORY - must be one of `detailed`, `summary`, or `transaction`.
employee | text | The employee code to filter expense claims for.
department | text | Specify one or more department names (separated by commas) to only show expenses within that department.
location | text | Specify one or more location names (separated by commas) to only show expenses within those locations.
expense_date_from | date | Starting date of expense claims to report for.
expense_date_to | date | Ending date of expense claims to report for.
submitted_date_from | date | Starting date of expense claim submission dates to report for.
submitted_date_to | date | Ending date of expense claim submission dates to report for.
approved_date_from | date | Starting date of approval for expense claims to report for.
approved_date_to | date | Ending date of approval for expense claims to report for.
status | text | Expense claim status to filter for, must be one of `submitted`, `approved`, `pending` or `rejected`.
is_paid | true/false | Filter expense claims on whether they have been paid or not.
expense_category | text | The expense category name to filter expenses for.
project | text | The project name to filter expenses for.


### Examples

To get a detailed list of all expenses for employee code 01985:

`GET https://api.hrpartner.io/expenses?report_type=detailed&employee=A12345`

To get a summary of all expenses for the 'Warehouse' department submitted in November 2022:

`GET https://api.hrpartner.io/expenses?report_type=summary&department=Warehouse&submitted_date_from=2022-11-01&submitted_date_to=2022-11-30`

To get a transaction list of all expense items that are paid for the project 'ACME Kitchen':

`GET https://api.hrpartner.io/expenses?report_type=transaction&is_paid=true&project=ACME Kitchen`

