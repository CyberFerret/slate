# Employee Birthdays & Anniversaries

The following section details how to generate a list of employee birthdays, as well as a list of employee anniversaries from our system.



## Birthdays

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/birthdays'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/birthdays"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;

var client = new Client();
var endpoint = "https://api.hrpartner.io/birthdays";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
[
	{
		"code": "GREGL",
		"first_names": "Lesa",
		"last_name": "Gregory",
		"full_name": "Gregory, Lesa",
		"date_of_birth": "3rd Nov 1988",
		"age": "34 years",
		"gender_identity": "Female",
		"is_active": true,
		"is_terminated": false,
		"is_on_leave": false,
		"department": "Customer Support",
		"location": "Perth",
		"position": "Customer Service Rep",
    "group": "Middleton Branch",
		"employment_status": "Full Time",
		"avatar": "https://s3.amazonaws.com/hrpartner/_5jGmaQIuOL3uqyjf7Y22Q%2Femployee%2F28%2FLesa%20Gregory.jpg",
		"email": "devan+lesa@blaze.com.au",
		"started_at": "2009-04-11",
		"finished_at": null
	},
	{
		"code": "FLETC",
		"first_names": "Curtis",
		"last_name": "Fletcher",
		"full_name": "Fletcher, Curtis",
		"date_of_birth": "5th Nov 1998",
		"age": "24 years",
		"gender_identity": "Male",
		"is_active": true,
		"is_terminated": false,
		"is_on_leave": false,
		"department": "Production",
		"location": "Main Office",
    "group": "Gotham Branch",
		"position": "Assembly Line Worker",
		"employment_status": "Casual",
		"avatar": "https://s3.amazonaws.com/hrpartner/_5jGmaQIuOL3uqyjf7Y22Q%2Femployee%2F32%2FCurtis%20Fletcher.jpg",
		"email": "fletcher@mailinator.com",
		"started_at": "2015-09-11",
		"finished_at": null
	}
]
```

The Birthday request will return an abbreviated employee list with some core details, as well as their calculated age at the time of making the call.

Please note that this call will only return Active, Non-Terminated employees.

### HTTP Request

`GET https://api.hrpartner.io/birthdays`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
department | text | Specify one or more department names (separated by commas) to only show employees within those departments.
location | text | Specify one or more location names (separated by commas) to only show employees withi those locations.
position | text | Specify one or more position names (separated by commas) to only show employees withi those positions.
employment status | text | Specify one or more employment status names (separated by commas) to only show employees withi those employment statuses.
start_month | number | Specify the starting month of the year to get results for (1=Jan, 2=Feb ... 12=Dec).
end_month | number | Specify the ending month of the year to get results for (1=Jan, 2=Feb ... 12=Dec).
selected_year | number | Specify the 4 digit selected year to print the report for (future years will forecase the employee age).


### Examples

To get a list of all employee birthdays for the 'Finance' and 'Warehouse' departments:

`GET https://api.hrpartner.io/birthdays?department=Finance,Warehouse`

To get all employee birthdays from January to March in the current year:

`GET https://api.hrpartner.io/birthdays?start_month=1&end_month=3`

To get all employee birthdays in October 2023:



## Anniversaries

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/anniversaries'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/anniversaries"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;

var client = new Client();
var endpoint = "https://api.hrpartner.io/anniversaries";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
[
	{
		"code": "LANEB",
		"first_names": "Bella",
		"last_name": "Lane",
		"full_name": "Lane, Bella",
		"date_of_birth": "6th Mar 1989",
		"gender_identity": "Female",
		"is_active": true,
		"is_terminated": false,
		"is_on_leave": true,
		"department": "Personnel",
		"location": "Sydney",
    "group": "Middleton Branch"
		"position": "Intern",
		"employment_status": "Casual",
		"avatar": "https://s3.amazonaws.com/hrpartner/_5jGmaQIuOL3uqyP6uyP9Q%2Femployee%2F9%2FBella%20Lane.jpg",
		"email": "bella@mailinator.com",
		"started_at": "2014-11-07",
		"finished_at": null,
		"years_worked": 8
	},
	{
		"code": "40100",
		"first_names": "Barry",
		"last_name": "Aardvark",
		"full_name": "Aardvark, Barry",
		"date_of_birth": "10th Aug 1990",
		"gender_identity": "Male",
		"is_active": true,
		"is_terminated": false,
		"is_on_leave": false,
		"department": "Administration",
		"location": "Main Office",
    "group": "Stanstead Branch",
		"position": "Storeperson",
		"employment_status": "Full Time",
		"avatar": "https://s3.amazonaws.com/hrpartner/_5jGmaQIuOL3uqy6uyP92Q%2Femployee%2FPpm%2Faardvark--barry.png",
		"email": "barry.aardvark@mailinator.com",
		"started_at": "2019-11-07",
		"finished_at": null,
		"years_worked": 3
	},
	{
		"code": "LAYMD",
		"first_names": "Daniel",
		"last_name": "Layman",
		"full_name": "Layman, Daniel",
		"date_of_birth": "",
		"gender_identity": "Male",
		"is_active": true,
		"is_terminated": false,
		"is_on_leave": false,
		"department": "Development",
		"location": "Remote Office",
    "group": "Stanstead Branch",
		"position": "Programmer",
		"employment_status": "Part Time",
		"avatar": "https://s3.amazonaws.com/hrpartner/_5jGmaQIuOL3uqyP6uyP9Q%2Femployee%2FQo5%2Flayman--daniel.png",
		"email": "daniellayman@mailinator.com",
		"started_at": "2017-11-14",
		"finished_at": null,
		"years_worked": 5
	}
]
```

The Anniversary request will return an abbreviated employee list with some core details, as well as their length of employment at the time of making the call.

Please note that this call will only return Active, Non-Terminated employees.

### HTTP Request

`GET https://api.hrpartner.io/anniversaries`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
department | text | Specify one or more department names (separated by commas) to only show employees within those departments.
location | text | Specify one or more location names (separated by commas) to only show employees within those locations.
position | text | Specify one or more position names (separated by commas) to only show employees within those positions.
group | text | Specify one or more group names (separated by commas) to only show eployees within those groups.
employment status | text | Specify one or more employment status names (separated by commas) to only show employees withi those employment statuses.
start_month | number | Specify the starting month of the year to get results for (1=Jan, 2=Feb ... 12=Dec).
end_month | number | Specify the ending month of the year to get results for (1=Jan, 2=Feb ... 12=Dec).
selected_year | number | Specify the 4 digit selected year to print the report for (future years will forecast the employee length of service).


### Examples

To get a list of all employee anniversaries for 'Full Time' and 'Casual' employee positions:

`GET https://api.hrpartner.io/anniversaries?position=Full Time,Casual`

To get all employee anniversaries from July to December in the current year:

`GET https://api.hrpartner.io/anniversaries?start_month=7&end_month=12`

To get all employee anniversaries in March 2023 for the 'London' location:

`GET https://api.hrpartner.io/anniversaries?location=London&start_month=3&end_month=3&selected_year=2023`


