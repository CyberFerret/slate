# Employees

## Get All Employees

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/employees'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/employees"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/employees";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1001,
    "code": "40100",
    "first_names": "Barry",
    "last_name": "Aardvark",
    "full_name": "Aardvark, Barry",
    "date_of_birth": "1990-08-10",
    "gender_identity": "Male",
    "is_active": true,
    "is_terminated": false,
    "is_on_leave": false,
    "pay_point": "",
    "department": "Administration",
    "location": "Main Office",
    "position": "Storeperson",
    "employment_status": "Full Time",
    "avatar": "https://s3.amazonaws.com/hrpartner/_5jGmaQIuOL3uqyP6MU22Q/employee/Ppm/aardvark--barry.png",
    "email": "barry.aardvark@mailinator.com",
    "started_at": "0019-11-07",
    "finished_at": null
  },
  {
    "id": 1003,
    "code": "40101",
    "first_names": "Yolanda",
    "last_name": "Bbardin",
    "full_name": "Bbardin, Yolanda",
    "date_of_birth": "1989-05-13",
    "gender_identity": "Female",
    "is_active": true,
    "is_terminated": false,
    "is_on_leave": false,
    "pay_point": "",
    "department": "Administration",
    "location": "Main Office",
    "position": "Accounts Clerk",
    "employment_status": "Full Time",
    "avatar": "https://s3.amazonaws.com/hrpartner/_5jGmaQIuOL3uqyP6MU22Q/employee/EEM/bbardin--yolanda.png",
    "email": "yolanda@mailinator.com",
    "started_at": "0019-11-08",
    "finished_at": null
  },
  {
    "id": 1012,
    "code": "ANTHS",
    "first_names": "Susan",
    "last_name": "Anthony",
    "full_name": "Anthony, Susan",
    "date_of_birth": null,
    "gender_identity": "Female",
    "is_active": false,
    "is_terminated": true,
    "is_on_leave": false,
    "pay_point": "",
    "department": "Warehouse",
    "location": "Perth Branch",
    "position": "Driver",
    "employment_status": "Casual",
    "avatar": "",
    "email": "susananthony@mailinator.com",
    "started_at": "2017-08-21",
    "finished_at": "2020-03-17"
  }
]
```

This endpoint retrieves all employees in the system.

### HTTP Request

`GET https://api.hrpartner.io/employees`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
search | text | Return only employees whose first or last names match this search text.
department | text | Specify one or more department names (separated by commas) to only show employees within that department.
location | text | Only return employees within this location.
position | text | Only return employees with this position description.
employment_status | text | Only return employees with this employment status.
gender_identity | text (M/F or extended identity full string) | Only return employees with this gender.
pay_point | text | Only return employees that have this pay point identifier.
birth_date_from, birth_date_to | date (yyyy-mm-dd) | Return employees whose birth date falls between these two dates (inclusive).
start_date_from, start_date_to | date (yyyy-mm-dd) | Return employees whose starting employment date falls between these two dates (inclusive).
end_date_from, end_date_to | date (yyyy-mm-dd) | Return employees whose termination/ending date falls between these two dates (inclusive).
tag | text | Only return employees who have this tag (single tag only).
is_active | true/false | Choose whether to return only active employees.
is_terminated | true/false | Choose whether to return only terminated employees.
can_logon | true/false | Choose whether to return only employee who can logon to their portal.
reports_to | text | Only return employees who report to the employee with this Employee Code


### Examples

To get a list of all employees in the "London" location who are not terminated:

`GET https://api.hrpartner.io/employees?location=London&is_terminated=false`

To get all employees in either the "Admin Team" or "Warehouse" departments:

`GET https://api.hrpartner.io/employees?department=Admin Team,Warehouse`

To get all full time employees who started employment during March 2020:

`GET https://api.hrpartner.io/employees?start_date_from=2020-03-01&start_date_to=2020-03-31&employment_status=Full Time`

To get all employees who report to the person that has Employee Code "EMP001", who are not terminated:

`GET https://api.hrpartner.io/employees?is_terminated=false&reports_to=EMP001`


## Get A Specific Employee

```ruby
require 'rest-client'

header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}
endpoint = 'https://api.hrpartner.io/employee/'
employeecode = 'BLENA'

result = RestClient.get(endpoint + employeecode, header)

puts result
```

```shell
curl "https://api.hrpartner.io/employee/BLENA"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};
var endpoint = "https://api.hrpartner.io/employee/";
var employeecode = "BLENA"

client.get(endpoint + employeecode, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this:

```json
{
  "id": 1001,
  "code": "BLENA",
  "first_names": "Arthur",
  "last_name": "Blenkinshop",
  "full_name": "Blenkinshop, Arthur",
  "salutation": "",
  "avatar": "https://s3.amazonaws.com/hrpartner/_5jGmaQIuOL3uqyP6MU22Q/employee/sk8y65/ArthurBlenkinshop.jpg",
  "date_of_birth": "1988-02-23",
  "gender_identity": "Male",
  "pay_point": "",
  "tax_number": "",
  "started_at": "2009-05-22",
  "finished_at": "",
  "is_active": true,
  "is_terminated": false,
  "is_on_leave": true,
  "can_logon": true,
  "portal_username": "BLENA",
  "custom_data": {
    "annual-salary": 45000.0,
    "warnings-given": 0,
    "citizenship": "Other (Foreign)",
    "next-increment-due": "2016-03-22",
    "next-increment-amount": 2500.25,
    "training-category": "Pool A - Darwin",
    "training-cert-number": "K123",
    "usual-start-time": "08:00",
    "usual-end-time": "05:15",
    "favourite-books": "Fantasy fiction and historical novels.",
    "has-drivers-licence": true
  },
  "department": "Sales",
  "location": "Main Office",
  "position": "Warehouse Supervisor",
  "employment_status": "Full Time",
  "reports_to": "BURRS",
  "tags": [
    {
      "tag": "Smoker"
    },
    {
      "tag": "EOM Winner"
    },
    {
      "tag": "Picnic Committee"
    },
    {
      "tag": "Project Blenheim"
    }
  ],
  "employee_contacts": [
    {
      "id": 11,
      "type": "Mobile",
      "details": "+61 213 433442",
      "is_primary": true
    },
    {
      "id": 14,
      "type": "Email",
      "details": "arthurblenkinshop@mailinator.com",
      "is_primary": true
    },
    {
      "id": 16,
      "type": "Twitter",
      "details": "@theblenkinsop",
      "is_primary": false
    },
    {
      "id": 18,
      "type": "LinkedIn",
      "details": "linked.in/blenkinsop",
      "is_primary": false
    },
    {
      "id": 500,
      "type": "Email",
      "details": "arthurathome@mailinator.com",
      "is_primary": false
    }
  ],
  "employee_addresses": [
    {
      "id": 1,
      "type": "Home",
      "address_1": "123 Main Street",
      "address_2": null,
      "suburb": "Marrickville",
      "state": "WA",
      "post_code": "8089",
      "country": "Australia"
    },
    {
      "id": 3,
      "type": "Delivery",
      "address_1": "2/35B William Street",
      "address_2": "St. Macarthur Building",
      "suburb": "Tennville",
      "state": "LO",
      "post_code": "90-004",
      "country": "New Zealand"
    }
  ]
}
```

This endpoint retrieves a single employee from the system using their **_Employee Code_**.

### HTTP Request

`GET https://api.hrpartner.io/employee/{employeeCode}`

This call will return a lot more detail about an individual employee, including all their contact details, address details, as well as any custom fields that you may have created within your HR Partner company.


<aside class="notice">Tip: You can use the <code>GET /employees</code> call to get a list of all employees, then extract the <em>code</em> field from the results to fetch individual employees.</aside>


## Update/Add An Employee

```ruby
require 'rest-client'

# Update Arthur's record with tax number, update custom fields with new salary and work times, add contractor tag, change mobile number and add new email
postbody = {
  "code": "BLENA",
  "tax_number": "112-509-6867",
  "can_logon": true,
  "portal_username": "ABLENK001",
  "custom_data": {
    "annual-salary": 62500.00,
    "usual-start-time": "09:00",
    "usual-end-time": "16:45",
    "favourite-books": "Super hero comics.",
  },
  "employment_status": "Contract",
  "tags": [
    {
      "tag": "External Contractor"
    }
  ],
  "employee_contacts": [
    {
      "id": 11,
      "type": "Mobile",
      "details": "+61 444 982311",
      "is_primary": true
    },
    {
      "type": "Email",
      "details": "blenkarthur@test.com",
      "is_primary": false
    }
  ]  
}

header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d', :body => postbody}
endpoint = 'https://api.hrpartner.io/employee/'
employeecode = 'BLENA'

result = RestClient.post(endpoint + employeecode, header)

puts result
```

```shell
curl "https://api.hrpartner.io/employee/BLENA"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
  -H "Content-Type: application/json"
  -X POST
  -d '{"code": "BLENA","tax_number": "112-509-6867","can_logon": true,"portal_username": "ABLENK001", \
  "custom_data": {"annual-salary": 62500.00,"usual-start-time": "09:00","usual-end-time": "16:45","favourite-books": "Super hero comics.",}, \
  "employment_status": "Contract","tags": [{"tag": "External Contractor"}], \
  "employee_contacts": [{"id": 11,"type": "Mobile","details": "+61 444 982311","is_primary": true},{"type": "Email","details": "blenkarthur@test.com","is_primary": false}]}'
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();

// Update Arthur's record with tax number, update custom fields with new salary and work times, add contractor tag, change mobile number and add new email
var postbody = postbody = {
  "code": "BLENA",
  "tax_number": "112-509-6867",
  "can_logon": true,
  "portal_username": "ABLENK001",
  "custom_data": {
    "annual-salary": 62500.00,
    "usual-start-time": "09:00",
    "usual-end-time": "16:45",
    "favourite-books": "Super hero comics.",
  },
  "employment_status": "Contract",
  "tags": [
    {
      "tag": "External Contractor"
    }
  ],
  "employee_contacts": [
    {
      "id": 11,
      "type": "Mobile",
      "details": "+61 444 982311",
      "is_primary": true
    },
    {
      "type": "Email",
      "details": "blenkarthur@test.com",
      "is_primary": false
    }
  ]  
}

var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}, body: postbody};
var endpoint = "https://api.hrpartner.io/employee/";
var employeecode = "BLENA"

client.post(endpoint + employeecode, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this:

```json
{
  "code": "BLENA",
  "first_names": "Arthur",
  "last_name": "Blenkinshop",
  "full_name": "Blenkinshop, Arthur",
  "salutation": "",
  "avatar": "https://s3.amazonaws.com/hrpartner/_5jGmaQIuOL3uqyP6MU22Q/employee/sk8y65/ArthurBlenkinshop.jpg",
  "date_of_birth": "1988-02-23",
  "gender_identity": "Male",
  "pay_point": "",
  "tax_number": "112-509-6867",
  "started_at": "2009-05-22",
  "finished_at": "",
  "is_active": true,
  "is_terminated": false,
  "is_on_leave": true,
  "can_logon": true,
  "portal_username": "ABLENK001",
  "custom_data": {
    "annual-salary": 62500.00,
    "warnings-given": 0,
    "citizenship": "Other (Foreign)",
    "next-increment-due": "2016-03-22",
    "next-increment-amount": 2500.25,
    "training-category": "Pool A - Darwin",
    "training-cert-number": "K123",
    "usual-start-time": "09:00",
    "usual-end-time": "16:45",
    "favourite-books": "Super hero comics.",
    "has-drivers-licence": true
  },
  "department": "Sales",
  "location": "Main Office",
  "position": "Warehouse Supervisor",
  "employment_status": "Contract",
  "reports_to": "BURRS",
  "tags": [
    {
      "tag": "Smoker"
    },
    {
      "tag": "EOM Winner"
    },
    {
      "tag": "Picnic Committee"
    },
    {
      "tag": "Project Blenheim"
    },
    {
      "tag": "External Contractor"
    }
  ],
  "employee_contacts": [
    {
      "id": 11,
      "type": "Mobile",
      "details": "+61 444 982311",
      "is_primary": true
    },
    {
      "id": 14,
      "type": "Email",
      "details": "arthurblenkinshop@mailinator.com",
      "is_primary": true
    },
    {
      "id": 16,
      "type": "Twitter",
      "details": "@theblenkinsop",
      "is_primary": false
    },
    {
      "id": 18,
      "type": "LinkedIn",
      "details": "linked.in/blenkinsop",
      "is_primary": false
    },
    {
      "id": 500,
      "type": "Email",
      "details": "arthurathome@mailinator.com",
      "is_primary": false
    },
    {
      "id": 621,
      "type": "Email",
      "details": "blenkarthur@test.com",
      "is_primary": false
    }
  ],
  "employee_addresses": [
    {
      "id": 1,
      "type": "Home",
      "address_1": "123 Main Street",
      "address_2": null,
      "suburb": "Marrickville",
      "state": "WA",
      "post_code": "8089",
      "country": "Australia"
    },
    {
      "id": 3,
      "type": "Delivery",
      "address_1": "2/35B William Street",
      "address_2": "St. Macarthur Building",
      "suburb": "Tennville",
      "state": "LO",
      "post_code": "90-004",
      "country": "New Zealand"
    }
  ]
}
```


This endpoint either updates an existing employee, or adds a new employee (if the **_employeeCode_** does not exist).

### HTTP Request

`POST https://api.hrpartner.io/employee/{employeeCode}`

A successful POST will return an employee object (see the `GET /employee` call above) upon successful modification or addition.

### POST Body

The JSON packet that can be POSTed to the endpoint is essentially the same as the JSON that you receive from the GET call to the `/employee` endpoint.

Parameter | Type | Description
--------- | ---- | -----------
code<sup>*</sup> | text | The employee code
first_names | text | The first (and optionally, middle) name of the employee
last_name | text | The surname of the employee
full_name | text | The combines name of the employee (i.e. _First Last_ or _Last, First_)
salutation | text | Any greeting or salutation that you will use for the employee
date_of_birth | yyyy-mm-dd | Employee's date of birth in yyyy-mm-dd format
gender_identity | M/F or text | Either M or F, or if extended gender identities is turned on for the company, then the full text of the gender identity
pay_point | text | A reference for the employee's pay point
tax_number | text | The SSN, TFN, National ID or other tax identifier for the employee
started_at | yyyy-mm-dd | The date the employee started with the company
finished_at | yyyy-mm-dd | The date the employee was terminated or left the company
is_active | true/false | Flag whether the employee is active in HR Partner
is_terminated | true/false | Flag whether the employee is terminated in HR Partner
can_logon | true/false | Flag whether the employee can log on to their employee portal
portal_username | text | Employee's username for the portal
custom_data | object | See [**Custom Data**](#custom-data) structure below
department<sup>+</sup> | text | Department name that the employee belongs to
location<sup>+</sup> | text | Location that the employee is in
position<sup>+</sup> | text | Employee's position or job title
employment_status<sup>+</sup> | text| The employment status of the employee (i.e. Full Time, Part Time, Contractor etc.)
reports_to | text| The Employee Code of the person this employee reports to
tags | object | See [**Tags**](#tags) structure below
employee_contacts | object | See [**Employee Contacts**](#employee-contacts) structure below
employee_addresses | object | See [**Employee Addresses**](#employee-addresses) structure below


_<sup>*</sup> - Mandatory (required) field_

_<sup>+</sup> - If the field contains data that isn't already in HR Partner, it will be added to the list of drop down options_

Please note that the employee code is also required in the POST body as well as the URL for added verification and security.

#### Custom Data

The `custom_data` object within the employee data object will contain the field names and field contents of any custom fields that you have added to your HR Partner company.  Probably the best option is to execute a `GET` call on the `/employee/{employeeCode}` endpoint to get a current employee object and look at the structure of it to ascertain the exact structure of the object that needs to get sent back in the `POST` call.

<aside class="success">
  <strong>Note:</strong> You don't need to have ALL the custom fields in the <code>custom_data</code> object.  You only need to have the fields you want to update, and any fields not included will not be modified.
</aside>

#### Tags

The `tags` object contains an array of custom tags that you can allocate to the employee.

Parameter | Type | Description
--------- | ---- | -----------
tag | text | Tag name

Please note the construction of this object carefully.  It is not simply an array of strings, but rather an array of objects (see example of fetched employee data above).

If you use a tag that doesn't exist in HR Partner, that tag will get added to the list of tags, as well as being allocated to the employee.


#### Employee Contacts

This object contains the various contact items against the employee.

Parameter | Type | Description
--------- | ---- | -----------
id | number | The internal ID number of the contact data. If included, the contact details will be **updated**. If omitted, the contact details will be **added**
type | text | Must be one of: _Phone, Email, Mobile, Fax, Pager, Facebook, Twitter, Google+, LinkedIn, Skype, Instagram, GitHub_
details<sup>*</sup> | text | The actual contact details (email address or number etc.)
is_primary | true/false | Flag for whether this address is primary (will be used as default address for system emails or SMSs) 


#### Employee Addresses

This object contains the various address data against the employee.

Parameter | Type | Description
--------- | ---- | -----------
id | number | The internal ID number of the address. If included, the address details will be **updated**. If omitted, the address details will be **added**
type | text | Must be one of: _Home, Postal, Work, Delivery, Next of Kin, Visiting_
address_1 | text | First line of their address
address_2 | text | optional second line of their address
suburb | text | Either the suburb name or city name
state | text | The state or county name
post_code | text | Contains the zip or postal code
country | text | Must contain the valid name of a country

<aside class="warning">
  <strong>Note:</strong> At this stage, you CANNOT delete a tag, contact or address record that is against an employee via the API.
</aside>


