---
title: HR Partner API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - javascript

toc_footers:

  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the HR Partner API documentation.  This site is designed for developers or advanced users of HR Partner to be able to create mini apps or routines to read (and sometimes write) information from our system.

We have created some short code snippets here using some popular languages in order to showcase how to use the API.

You must have an active trial or paid subscription to HR Partner in order to be able to use or test the API.  Sign up for an account now at [www.hrpartner.io](https://www.hrpartner.io)

# Authentication

> To authorize, use this code:

```ruby
# With Ruby, you need to pass the api key in the header with each request
require 'rest-client'

endpoint = 'https://api.hrpartner.io/employees'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```


```shell
# With shell, you can just pass the correct header with each request
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

> Make sure to replace `ee095c2f58da4f36d087ca7794384f4d` with your API key.

HR Partner requires a unique API key to ensure security of any calls to our API.  Every HR Partner company is issued a randomly generated API key that can be accessed by going to **Setup -> Configure -> Integrations** within the main menu (Note: You will have to have full access rights to HR Partner in order to access this menu).  You will also need to activate API access to your company, which is turned off by default for protection of your data.

Always keep your API key safe and secure like you would your password.  Anyone with your API key can access your company data, including all employee information and attachments etc.

If you suspect that your API key has been compromised, you can generate a new one within HR Partner, or else you can turn off API access to your company from the same menu area.

Your API key _must_ be included in all calls to our API gateway, in the header of each call as follows:

`x-api-key:ee095c2f58da4f36d087ca7794384f4d`

<aside class="notice">
You must replace <code>ee095c2f58da4f36d087ca7794384f4d</code> with your personal API key.
</aside>


# Endpoint

The HR Partner API supports a simplified REST protocol.  You may make GET, POST and DELETE calls against our REST endpoint at:

**https://api.hrpartner.io/**

All calls to the endpoint _must_ be made using the HTTPS secure protocol.  Calls made over HTTP will either be automatically re-routed to HTTPS or else be ignored.

# Disclaimer

Note: The API is still in Beta at this point in time, so the information below is subject to change with little notice.  Where possible, we will try not to make changes to our API interface which will break anything that was written using the older spec, but we reserve the right to make changes to improve performance or improve security without advanced notification during the Beta phase.


---

# Company

```ruby
require 'rest-client'

header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}
endpoint = 'https://api.hrpartner.io/company'

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/company"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};
var endpoint = "https://api.hrpartner.io/company";

client.get(endpoint, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this:

```json
{
  "name": "Acme Industries",
  "slug": "adme-industries",
  "logo_image_link": "AyJfTPg769sI1wVSxQVwBQ/logo/acme_logo.png",
  "subdomain": "acme",
  "subscribed": true,
  "subscribed_until": "2099-03-21T00:00:00+00:00",
  "employee_limit": 50,
  "total_employees": 31,
  "active_employees": 26,
  "timezone": "Australia/Sydney",
  "sms_credits": 1.0
}
```

This endpoint retrieves your basic company data from HR Partner.

### HTTP Request

`GET https://api.hrpartner.io/company`

This call will return basic company information from HR Partner, including the company name, your subscription expiry information and employee counts.  It is useful for validating that you are communicating with the correct HR Partner company.




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


### Examples

To get a list of all employees in the "London" location who are not terminated:

`GET https://api.hrpartner.io/employees?location=London&is_terminated=false`

To get all employees in either the "Admin Team" or "Warehouse" departments:

`GET https://api.hrpartner.io/employees?department=Admin Team,Warehouse`

To get all full time employees who started employment during March 2020:

`GET https://api.hrpartner.io/employees?start_date_from=2020-03-01&start_date_to=2020-03-31&employment_status=Full Time`


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




# Employee Data

The following sections contain the methods required to read the sub module or category data for each employee.  At the current time, we only support reading of data from these modules, but a future version of the API may include write back ability.



## Absences

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/absences'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/absences"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/absences";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 14,
    "absence_reason": "Sick Leave",
    "description": "High fever",
    "absence_date": "2015-05-05",
    "return_date": "2015-05-07",
    "duration": 3.0,
    "physician": "Dr. Cromby",
    "certificate_number": "58475849887",
    "absence_status": "Recovered",
    "comments": "",
    "employee": {
      "code": "BUTTJ",
      "first_names": "James",
      "last_name": "Butterworth",
      "full_name": "Butterworth, James",
      "department": "Production"
    }
  },
  {
    "id": 5,
    "absence_reason": "Bereavement Leave",
    "description": "Attended auntie's funeral",
    "absence_date": "2015-07-09",
    "return_date": "2015-07-09",
    "duration": 2.0,
    "physician": "",
    "certificate_number": "",
    "absence_status": "Completed",
    "comments": "",
    "employee": {
      "code": "BLENA",
      "first_names": "Arthur",
      "last_name": "Blenkinshop",
      "full_name": "Blenkinshop, Arthur",
      "department": "Sales"
    },
    "attachments": [
      {
        "description": "Doctors Note 2015-07-10.pdf",
        "url": "_5jGmaQIuOL3uqyP6MU22Q/attachments/kPbSM9Mss5YXw37x2zNGFw/Doctors Note 2015-07-10.pdf",
        "size": 3601929
      }
    ]
  },
  {
    "id": 12,
    "absence_reason": "Sick Leave",
    "description": "Not feeling well",
    "absence_date": "2015-08-11",
    "return_date": "2015-08-12",
    "duration": 2.0,
    "physician": "Dr. Zhivago",
    "certificate_number": "T059457487",
    "absence_status": "Completed",
    "comments": "",
    "employee": {
      "code": "BUTTJ",
      "first_names": "James",
      "last_name": "Butterworth",
      "full_name": "Butterworth, James",
      "department": "Production"
    }
  }
]
```

The Absences module contains the records for each employee's leave or vacation time taken off.

### HTTP Request

`GET https://api.hrpartner.io/absences`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
employee | text | Specify the employee code to only see the absence records for that particular employee.
department | text | Specify one or more department names (separated by commas) to only show employee absences within that department.
location | text | Only return employees within this location.
absence_reason | text | Return only absence records with this particular absence reason.
duration_from, duration_to | number | Return only leave records with a duration between these values (inclusive).
physician | text | Return record with this partial text in the physician name field.
certificate_number | text | Return records with this text within the certificate field.
absence_status | text | Return records which have this absence status set.
comments | text | Search for this text within the comments field and return those.
absence_date_from, absence_date_to | date (yyyy-mm-dd) | Return leave records that fall between these two dates (inclusive).

### Examples

To get a list of all absence records for employee whose code is 'JONES':

`GET https://api.hrpartner.io/absences?employee=JONES`

To get all sick leave records approved by Dr. Smith:

`GET https://api.hrpartner.io/absences?physician=Smith&absence_reason=Sick Leave`

To get all 'Approved' leave records that occured during March 2020:

`GET https://api.hrpartner.io/absences?absence_date_from=2020-03-01&absence_date_to=2020-03-31&absence_status=Approved`

### Attachments

If an absence record includes attachments, they will be returned as an object array underneath the main absence record.  The structure of this object is:

Parameter | Type | Description
--------- | ---- | -----------
description | text | The file name
url | text | The URL path to the file
size | number | The size of the file in bytes



## Assets

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/assets'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/assets"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/assets";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 6,
    "asset_type": "Mobile Phones",
    "description": "iPhone 6 (Black)",
    "asset_identifier": "P90446",
    "serial_number": "A908573",
    "out_date": "2015-10-28",
    "in_date": null,
    "employee": {
      "code": "BLENA",
      "first_names": "Arthur",
      "last_name": "Blenkinshop",
      "full_name": "Blenkinshop, Arthur",
      "department": "Sales"
    }
  },
  {
    "id": 8,
    "asset_type": "Vehicle",
    "description": "Mazda 3",
    "asset_identifier": "V944",
    "serial_number": "4738342923846673",
    "out_date": "2015-10-01",
    "in_date": "2015-10-31",
    "employee": {
      "code": "BLACK",
      "first_names": "Katrina",
      "last_name": "Black",
      "full_name": "Black, Katrina",
      "department": "Administration"
    }
  },
  {
    "id": 9,
    "asset_type": "Computer",
    "description": "Apple Macbook Pro (2009)",
    "asset_identifier": "PC344",
    "serial_number": "Y847587-AA",
    "out_date": "2015-10-02",
    "in_date": "2015-10-29",
    "employee": {
      "code": "BLENA",
      "first_names": "Arthur",
      "last_name": "Blenkinshop",
      "full_name": "Blenkinshop, Arthur",
      "department": "Sales"
    }
  }
]  
```

The Assets module contains the records for company equipment that is on loan to the employee.

### HTTP Request

`GET https://api.hrpartner.io/assets`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
employee | text | Specify the employee code to only see the asset records for that particular employee.
department | text | Specify one or more department names (separated by commas) to only show employee assets within that department.
description | text | Return only assets with this partial text within the description field.
asset_identifier | text | Return only assets which have this text within the identifier field.
serial_number | text | Return only assets which have this text within the serial number field.
asset_type | text | Select only assets which have this type.
out_date_from, out_date_to | date (yyyy-mm-dd) | Select only assets that went out (allocated to the employee) between these two dates (inclusive).
in_date_from, in_date_to | date (yyyy-mm-dd) | Select only assets that came back to the company between these two dates (inclusive).

### Examples

To get a list all asset records for employees in the department 'Finance':

`GET https://api.hrpartner.io/assets?department=Finance`

To find all records which have the word 'Apple' within the description, and are of type 'Phone':

`GET https://api.hrpartner.io/assets?description=Apple&asset_type=Phone`

To see all assets that are due back in during March 2020:

`GET https://api.hrpartner.io/assets?in_date_from=2020-03-01&in_date_to=2020-03-31`

### Attachments

If an asset record includes attachments, they will be returned as an object array underneath the main asset record.  The structure of this object is:

Parameter | Type | Description
--------- | ---- | -----------
description | text | The file name
url | text | The URL path to the file
size | number | The size of the file in bytes



## Attachments

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/assets'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/assets"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/assets";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 7,
    "description": "My Cat.jpeg",
    "url": "_5jGmaQIuOL3uqyP6MU22Q/attachments/t3FfZo45ytnaUedhspSUuQ/My Cat.jpeg",
    "module": "note",
    "module_id": 25,
    "size": 6417,
    "uploaded_date": "2015-10-18T13:56:25+00:00",
    "employee": {
      "code": "BLENA",
      "first_names": "Arthur",
      "last_name": "Blenkinshop"
    }
  },
  {
    "id": 8,
    "description": "EmploymentContract002",
    "url": "_5jGmaQIuOL3uqyP6MU22Q/attachments/biFFfaPJqgwlWbcbPVWTzQ/EmploymentContract002",
    "module": "review",
    "module_id": 2,
    "size": 336892,
    "uploaded_date": "2015-10-18T14:13:32+00:00",
    "employee": {
      "code": "BURRS",
      "first_names": "Stacey",
      "last_name": "Burridge"
    }
  },
  {
    "id": 10,
    "description": "kids.jpg",
    "url": "_5jGmaQIuOL3uqyP6MU22Q/attachments/9GanCSkAzi5jzr32Cc2YCA/kids.jpg",
    "module": "dependent",
    "module_id": 2,
    "size": 1785990,
    "uploaded_date": "2015-10-18T14:16:43+00:00",
    "employee": {
      "code": "BLENA",
      "first_names": "Arthur",
      "last_name": "Blenkinshop"
    }
  }
]
```

The Attachments module contains the records for all file attachments for every employee within the company.

### HTTP Request

`GET https://api.hrpartner.io/attachments`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
employee | text | Specify the employee code to only see the attachments for that particular employee.
department | text | Specify one or more department names (separated by commas) to only show employee attachments within those departments.
description | text | Return only attachment with this partial text within the description (file name) field.
module | text | Return only attachments which belong to this particular module  (See [Modules](#modules) list in another section).
uploaded_date_from, uploaded_date_to | date (yyyy-mm-dd) | Select only attachments that were uploaded between these two dates (inclusive).

### Examples

To get a list all attachments for employees with the code 'BLENA':

`GET https://api.hrpartner.io/attachments?employee=BLENA`

To find all attachments which have the word 'contract' within the file name, belong to the module 'review':

`GET https://api.hrpartner.io/attachments?description=contract&module=review`

To see all attachments that were uploaded on 23rd March 2020:

`GET https://api.hrpartner.io/attachments?uploaded_date_from=2020-03-23&uploaded_date_to=2020-03-23`



## Benefits

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/benefits'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/benefits"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/benefits";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "description": "A1Health Plan",
    "start_date": "2017-03-01",
    "end_date": "2018-02-28",
    "benefit_value": 3655.0,
    "benefit_value_period": "Year",
    "benefit_type": "Health Insurance",
    "benefit_provider": "MLC Health",
    "benefit_status": "Active",
    "comments": "Company health plan",
    "employee": {
      "code": "MILLS",
      "first_names": "Sally",
      "last_name": "Miller",
      "full_name": "Miller, Sally",
      "department": "Sales"
    }
  },
  {
    "id": 2,
    "description": "Tertiary Assist Program",
    "start_date": "2017-01-01",
    "end_date": "2017-12-31",
    "benefit_value": 600.0,
    "benefit_value_period": "Year",
    "benefit_type": "Educational Assistance",
    "benefit_provider": "BT University",
    "benefit_status": "Pending",
    "comments": "",
    "employee": {
      "code": "FISHL",
      "first_names": "Logan",
      "last_name": "Fisher",
      "full_name": "Fisher, Logan",
      "department": "Administration"
    },
    "attachments": [
      {
        "description": "FinAssistForm-F43.pdf",
        "url": "_5jGmaQIuOL3uqyP6MU22Q/attachments/NuDMMix__IgSJyqdW3BjpA/FinAssistForm-F43.pdf",
        "size": 74921
      }
    ]
  }
]
```

The Benefits module contains the records for any additional benefit or allowance plans that the employee may be on.

### HTTP Request

`GET https://api.hrpartner.io/benefits`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
employee | text | Specify the employee code to only see the benefit records for that particular employee.
department | text | Specify one or more department names (separated by commas) to only show employee benefits within that department.
benefit_type | text | Specify the benefit type to list only records matching this type.
benefit_status | text | Specify the benefit status to retrieve only records which matchi this status.
description | text | Return only benefits with this partial text within the description field.
comments | text | Return only benefits with this partial text within the comments field.
start_date_from, start_date_to | date (yyyy-mm-dd) | Select only benefits that started between these two dates (inclusive).
end_date_from, end_date_to | date (yyyy-mm-dd) | Select only benefits that finish between these two dates (inclusive).
benefit_value_from, benefit_value_to | number | Return only benefits with a value between these two parameters.
benefit_value_period | text | Retrieve only benefits which have this value period.

### Examples

To get a list all benefit records for employees in the department 'Sales' that have a status of 'After Tax':

`GET https://api.hrpartner.io/benefits?department=Sales&benefit_status=After Tax`

To find all benefit records which have the word 'Health' within the description, and are valued between $100.00 and $500.00 per month:

`GET https://api.hrpartner.io/benefits?description=Health&benefit_value_from=100&benefit_value_to=500&benefit_value_period=Month`

To see all benefits that started in the year 2020:

`GET https://api.hrpartner.io/benefits?start_date_from=2020-01-01&start_date_to=2020-12-31`

### Attachments

If a benefit record includes attachments, they will be returned as an object array underneath the main benefit record.  The structure of this object is:

Parameter | Type | Description
--------- | ---- | -----------
description | text | The file name
url | text | The URL path to the file
size | number | The size of the file in bytes



## Dependents

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/dependents'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/dependents"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/dependents";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 134,
    "dependent_type": "Son",
    "name": "William",
    "contact_details": "",
    "date_of_birth": "2009-03-11",
    "comments": "",
    "employee": {
      "code": "BLENA",
      "first_names": "Arthur",
      "last_name": "Blenkinshop",
      "full_name": "Blenkinshop, Arthur",
      "department": "Sales"
    },
    "attachments": [
      {
        "description": "10342961_10152816950947786_4977910610541866258_n.jpg",
        "url": "_5jGmaQIuOL3uqyP6MU22Q/attachments/mAn9-w8cEaE4Jfg2PqgSBg/10342961_10152816950947786_4977910610541866258_n.jpg",
        "size": 126615
      }
    ]
  },
  {
    "id": 189,
    "dependent_type": "Daughter",
    "name": "Sally-Anne",
    "contact_details": "",
    "date_of_birth": "2011-07-22",
    "comments": "His favourite daughter!",
    "employee": {
      "code": "BLENA",
      "first_names": "Arthur",
      "last_name": "Blenkinshop",
      "full_name": "Blenkinshop, Arthur",
      "department": "Sales"
    },
    "attachments": [
      {
        "description": "Sally.JPG",
        "url": "_5jGmaQIuOL3uqyP6MU22Q/attachments/biFFfaPJqgwlWbcbPVWTzQ/Sally.JPG",
        "size": 336892
      },
      {
        "description": "coincollection.jpg",
        "url": "_5jGmaQIuOL3uqyP6MU22Q/attachments/9GanCSkAzi5jzr32Cc2YCA/coincollection.jpg",
        "size": 1785990
      }
    ]
  },
  {
    "id": 211,
    "dependent_type": "Wife",
    "name": "Samantha",
    "contact_details": "0498 412556",
    "date_of_birth": "1974-12-16",
    "comments": "",
    "employee": {
      "code": "BURRS",
      "first_names": "Sally",
      "last_name": "Burridge",
      "full_name": "Burridge, Sally",
      "department": "Administration"
    }
  }
]
```

The Dependents module contains the records for any dependents, spouses, kids or family related to the employee.

### HTTP Request

`GET https://api.hrpartner.io/dependents`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
employee | text | Specify the employee code to only see the dependent records for that particular employee.
department | text | Specify one or more department names (separated by commas) to only show employee dependents within that department.
dependent_type | text | Specify the dependent type to list only records matching this type.
name | text | Return only dependents with this partial text within the name field.
contact_details | text | Return only dependents with this partial text within the contact details field.
comments | text | Return only dependents with this partial text within the comments field.
date_of_birth_from, date_of_birth_to | date (yyyy-mm-dd) | Select only dependents whose date of birth falls between these two dates (inclusive).


### Examples

To get a list all dependent records for employee with the code 'BURRS':

`GET https://api.hrpartner.io/dependents?employee=BURRS`

To find all dependent records who have the name of 'John':

`GET https://api.hrpartner.io/dependents?name=John`

### Attachments

If a dependent record includes attachments, they will be returned as an object array underneath the main dependent record.  The structure of this object is:

Parameter | Type | Description
--------- | ---- | -----------
description | text | The file name
url | text | The URL path to the file
size | number | The size of the file in bytes


## Education

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/education'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/education"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/education";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 2031,
    "institution": "Dutton High School",
    "commence_date": "2009-11-27",
    "completion_date": "2010-11-15",
    "education_type": "High School",
    "education_status": "No Result",
    "comments": null,
    "employee": {
      "code": "BLENA",
      "first_names": "Arthur",
      "last_name": "Blenkinshop",
      "full_name": "Blenkinshop, Arthur",
      "department": "Sales"
    }
  },
  {
    "id": 3499,
    "institution": "Farville Secondary College",
    "commence_date": "2012-01-25",
    "completion_date": "2012-02-29",
    "education_type": "Adult Education",
    "education_status": "Passed",
    "comments": null,
    "employee": {
      "code": "BLENA",
      "first_names": "Arthur",
      "last_name": "Blenkinshop",
      "full_name": "Blenkinshop, Arthur",
      "department": "Sales"
    }
  },
  {
    "id": 5150,
    "institution": "King Street High School",
    "commence_date": "1970-03-01",
    "completion_date": "1976-12-31",
    "education_type": "High School",
    "education_status": "Passed",
    "comments": null,
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

The Education module contains the records for any educational institutions that the employee may have attended _before_ they started with your company.

### HTTP Request

`GET https://api.hrpartner.io/education`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
employee | text | Specify the employee code to only see the education records for that particular employee.
department | text | Specify one or more department names (separated by commas) to only show employee educational records within that department.
education_type | text | Specify the education type to list only records matching this type.
education_status | text | Specify the education outcome or status to report for.
institution | text | Return only educational records with this partial text within the institution field.
qualification | text | Return only educational records with this partial text within the qualification field.
comments | text | Return only education details where the comments field contains this partial string.
commence_date_from, commence_date_to | date (yyyy-mm-dd) | Return only education records which commenced between these two dates (inclusive).
completion_date_from, completion_date_to | date (yyyy-mm-dd) | Select only education records which had a completion date that falls between these two dates (inclusive).

### Examples

To get a list all education records for employee with the code '00204':

`GET https://api.hrpartner.io/education?employee=BURRS`

To find all education records for employees who attended high school and passed:

`GET https://api.hrpartner.io/education?education_type=High School&education_status=Passed`

To find all education records in the year 2020 for employees in the Finance department:

`GET https://api.hrpartner.io/education?department=Finance&commence_date_from=2020-01-01&commence_date_to=2020-12-31`

### Attachments

If an education record includes attachments, they will be returned as an object array underneath the main education record.  The structure of this object is:

Parameter | Type | Description
--------- | ---- | -----------
description | text | The file name
url | text | The URL path to the file
size | number | The size of the file in bytes



## Grievances

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/grievances'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/grievances"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/grievances";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 7254,
    "grievance_type": "Complaint",
    "description": "Used bad language in conversation with customer",
    "reported_date": "2019-02-21",
    "actioned_by": "RR",
    "grievance_status": "Resolved",
    "comments": "",
    "employee": {
      "code": "GRANC",
      "first_names": "Craig",
      "last_name": "Grant",
      "full_name": "Grant, Craig",
      "department": "Sales"
    }
  },
  {
    "id": 7299,
    "grievance_type": "Harrassment",
    "description": "Inappropriate behaviour at company function",
    "reported_date": "2019-03-27",
    "actioned_by": "",
    "grievance_status": "Dismissed",
    "comments": "",
    "employee": {
      "code": "GRANC",
      "first_names": "Craig",
      "last_name": "Grant",
      "full_name": "Grant, Craig",
      "department": "Sales"
    }
  },
  {
    "id": 8013,
    "grievance_type": "Complaint",
    "description": "Colleagues lodged a complaint",
    "reported_date": "2019-09-03",
    "actioned_by": "Fred Jones",
    "grievance_status": "Inconclusive",
    "comments": "Others reported Kate being a bit rude today.",
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

The Grievance module contains the records for any complaints or harrasments or other grievances that have been recorded against your employee.

### HTTP Request

`GET https://api.hrpartner.io/grievances`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
employee | text | Specify the employee code to only see the grievance records for that particular employee.
department | text | Specify one or more department names (separated by commas) to only show employee grievance records within that department.
grievance_type | text | Specify the grievance type to list only records matching this type.
grievance_status | text | Specify the grievance outcome or status to report for.
description | text | Return only grievance records with this partial text within the institution field.
actioned_by | text | Return only grievance details where the 'actioned by' field containt this partial name.
reported_date_from, reported_date_to | date (yyyy-mm-dd) | Return only grievance records which reported between these two dates (inclusive).

### Examples

To get a list all grievance records for complaints:

`GET https://api.hrpartner.io/grievances?grievance_type=Complaint`

To find all grievance records for employees in the Warehouse department that were filed in March 2020:

`GET https://api.hrpartner.io/grievances?department=Warehouse&reported_date_from=2020-03-31&reported_date_to=2020-03-31`

To find all grievances that were actioned by John Smith with a resulting status of 'In Mediation':

`GET https://api.hrpartner.io/grievances?actioned_by=John Smith&grievance_status=In Mediation`

### Attachments

If a grievance record includes attachments, they will be returned as an object array underneath the main grievance record.  The structure of this object is:

Parameter | Type | Description
--------- | ---- | -----------
description | text | The file name
url | text | The URL path to the file
size | number | The size of the file in bytes



## Interviews

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/interviews'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/interviews"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/interviews";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1056,
    "interview_type": "Initial Interview",
    "description": "First interview",
    "interviewer": "Dr. Johnson",
    "interview_date": "2015-10-16",
    "comments": "This was a test interview",
    "employee": {
      "code": "BLENA",
      "first_names": "Arthur",
      "last_name": "Blenkinshop",
      "full_name": "Blenkinshop, Arthur",
      "department": "Sales"
    }
  },
  {
    "id": 1077,
    "interview_type": "Three Month Interview",
    "description": "3 Month Interview",
    "interviewer": "Jake Cartwright",
    "interview_date": "2015-10-06",
    "comments": "Sat down with Arthur for his 3 month interview - everything seemed to go OK, and he seemed happy.",
    "employee": {
      "code": "BLENA",
      "first_names": "Arthur",
      "last_name": "Blenkinshop",
      "full_name": "Blenkinshop, Arthur",
      "department": "Sales"
    }
  },
  {
    "id": 1096,
    "interview_type": "Induction Interview",
    "description": "Primary Interview for Bess",
    "interviewer": "Jim Hanson",
    "interview_date": "2015-07-01",
    "comments": "Everything seems fine.  Bess seems happy with how things are progressing at this stage.",
    "employee": {
      "code": "LUCAB",
      "first_names": "Bessi",
      "last_name": "Lucas",
      "full_name": "Lucas, Bessi",
      "department": "Sales"
    }
  },
  {
    "id": 2322,
    "interview_type": "Induction Interview",
    "description": "Saying hello to Katrina",
    "interviewer": "Jeff Garner",
    "interview_date": "2018-08-16",
    "comments": "Welcome to the company!",
    "employee": {
      "code": "BLACK",
      "first_names": "Katrina",
      "last_name": "Black",
      "full_name": "Black, Katrina",
      "department": "Warehouse"
    },
    "attachments": [
      {
        "description": "Welcome_Kit.pdf",
        "url": "_5jGmaQIuOL3uqyP6MU22Q/attachments/msqw63X2V3cFkL8ohJvnng/Welcome_Kit.pdf",
        "size": 84879
      },
      {
        "description": "Interview-notes-2018-08-16.pdf",
        "url": "_5jGmaQIuOL3uqyP6MU22Q/attachments/msqw63X2V3cFkL8ohJvnng/Interview-notes-2018-08-16.pdf",
        "size": 57321
      }
    ]
  }
]
```

The Interview module contains the records for any interviews or meetings that have been recorded against your employee.

### HTTP Request

`GET https://api.hrpartner.io/interviews`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
employee | text | Specify the employee code to only see the interview records for that particular employee.
department | text | Specify one or more department names (separated by commas) to only show employee interview records within that department.
interview_type | text | Specify the interview type to list only records matching this type.
description | text | Return only interview records with this partial text within the description field.
interviewer | text | Return only interview details where the 'interviewer' field contains this partial name.
interview_date_from, interview_date_to | date (yyyy-mm-dd) | Return only interview records which happened between these two dates (inclusive).

### Examples

To get a list all interview records of the type "First Interview":

`GET https://api.hrpartner.io/interview?interview_type=First Interview`

To find all interview records for employees in the Finance department that were filed in March 2020:

`GET https://api.hrpartner.io/interview?department=Finance&interview_date_from=2020-03-01&interview_date_to=2020-03-31`

To find all interviews that were carried out by Mary Jones and had the word 'promotion' in the description:

`GET https://api.hrpartner.io/interview?interviewer=Mary Jones&description=promotion`

### Attachments

If an interview record includes attachments, they will be returned as an object array underneath the main interview record.  The structure of this object is:

Parameter | Type | Description
--------- | ---- | -----------
description | text | The file name
url | text | The URL path to the file
size | number | The size of the file in bytes



## Notes

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/notes'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/notes"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/notes";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 3623,
    "note": "Need to schedule a meeting with James to discuss promotion",
    "created_date": "2015-11-02T00:33:02+00:00",
    "updated_date": "2015-11-02T00:33:02+00:00",
    "employee": {
      "code": "BUTTJ",
      "first_names": "James",
      "last_name": "Butterworth",
      "full_name": "Butterworth, James",
      "department": "Production"
    }
  },
  {
    "id": 3678,
    "note": "Buy a birthday present for Kylie!",
    "created_date": "2015-11-03T21:36:04+00:00",
    "updated_date": "2015-11-03T21:36:04+00:00",
    "employee": {
      "code": "HARVK",
      "first_names": "Kylie",
      "last_name": "Harvey",
      "full_name": "Harvey, Kylie",
      "department": "Customer Support"
    }
  },
  {
    "id": 3704,
    "note": "Stacey is looking to make a presentation to the team next week.",
    "created_date": "2015-11-06T02:20:01+00:00",
    "updated_date": "2015-11-06T02:20:01+00:00",
    "employee": {
      "code": "BURRS",
      "first_names": "Stacey",
      "last_name": "Burridge",
      "full_name": "Burridge, Stacey",
      "department": "Warehouse"
    }
  },
  {
    "id": 39,
    "note": "Rakesh wants to apply for Project Icarus as he thinks he will be a big help to that team in achieving their objectives.",
    "created_date": "2015-11-14T02:15:29+00:00",
    "updated_date": "2015-11-14T02:15:29+00:00",
    "employee": {
      "code": "PARAR",
      "first_names": "Rakesh",
      "last_name": "Parameswaran",
      "full_name": "Parameswaran, Rakesh",
      "department": "Administration"
    },
    "attachments": [
      {
        "description": "IMG_5711.PNG",
        "url": "_5jGmaQIuOL3uqyP6MU22Q/attachments/5mtnOdablhnE1c8XlfLOog/IMG_5711.PNG",
        "size": 275890
      },
      {
        "description": "Project Icarus Costings.csv",
        "url": "_5jGmaQIuOL3uqyP6MU22Q/attachments/wOOoi3-8V1_ugFuc2O5Sww/Project Icarus Costings.csv",
        "size": 3795
      }
    ]
  }
]
```

The Notes module contains any free forms notes that have been made against your employee.

### HTTP Request

`GET https://api.hrpartner.io/notes`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
employee | text | Specify the employee code to only see the notes for that particular employee.
department | text | Specify one or more department names (separated by commas) to only show employee notes within that department.
note | text | Return only notes with this partial text within the note text field.
created_date_from, created_date_to | date (yyyy-mm-dd) | Return notes that were created between these two dates (inclusive).
updated_date_from, updated_date_to | date (yyyy-mm-dd) | Return only notes which were updated/modified between these two dates (inclusive).

### Examples

To get a list all notes for John Smith (employee code SMITJ):

`GET https://api.hrpartner.io/notes?employee=SMITJ`

To find all notes created in March 2020:

`GET https://api.hrpartner.io/notes?created_date_from=2020-03-01&created_date_to=2020-03-31`

To find all notes that contain the word 'promotion' and were modified in the first week of March 2020:

`GET https://api.hrpartner.io/notes?note=promotion&updated_date_from=2020-03-01&updated_date_to=2020-03-08`

### Attachments

If a note includes attachments, they will be returned as an object array underneath the main note record.  The structure of this object is:

Parameter | Type | Description
--------- | ---- | -----------
description | text | The file name
url | text | The URL path to the file
size | number | The size of the file in bytes



## Positions

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/positions'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/positions"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/positions";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 3970,
    "position": "Operations Manager",
    "commence_date": "2015-10-03",
    "completion_date": null,
    "pay_level": "",
    "remuneration": 50000.0,
    "remuneration_period": "year",
    "comments": "Latest promotion",
    "employee": {
      "code": "BLENA",
      "first_names": "Arthur",
      "last_name": "Blenkinshop",
      "full_name": "Blenkinshop, Arthur",
      "department": "Sales"
    },
    "attachments": [
      {
        "description": "IMG_1816.JPG",
        "url": "_5jGmaQIuOL3uqyP6MU22Q/attachments/cNh0JliuSEvD4zoMGOsQxA/IMG_1816.JPG",
        "size": 457352
      },
      {
        "description": "IMG_1815.JPG",
        "url": "_5jGmaQIuOL3uqyP6MU22Q/attachments/cNh0JliuSEvD4zoMGOsQxA/IMG_1815.JPG",
        "size": 399918
      }
    ]
  },
  {
    "id": 4278,
    "position": "Driver",
    "commence_date": "2015-07-01",
    "completion_date": "2019-10-03",
    "pay_level": "",
    "remuneration": 45600.0,
    "remuneration_period": "year",
    "comments": "Due for a promotion on 5th Dec after a retraining.",
    "employee": {
      "code": "DUNND",
      "first_names": "Deanne",
      "last_name": "Dunn",
      "full_name": "Dunn, Deanne",
      "department": "Warehouse"
    }
  },
  {
    "id": 4299,
    "position": "Intern",
    "commence_date": "2017-03-01",
    "completion_date": null,
    "pay_level": "",
    "remuneration": 25000.0,
    "remuneration_period": "year",
    "comments": "",
    "employee": {
      "code": "FLETC",
      "first_names": "Curtis",
      "last_name": "Fletcher",
      "full_name": "Fletcher, Curtis",
      "department": "Production"
    }
  },
  {
    "id": 4351,
    "position": "Assembly Line Worker",
    "commence_date": "2017-04-12",
    "completion_date": "2017-05-22",
    "pay_level": "",
    "remuneration": 30000.0,
    "remuneration_period": "year",
    "comments": "",
    "employee": {
      "code": "FLETC",
      "first_names": "Curtis",
      "last_name": "Fletcher",
      "full_name": "Fletcher, Curtis",
      "department": "Production"
    }
  }
]
```

The Position module contains the records for any position or employment contracts that have been recorded against your employee.

### HTTP Request

`GET https://api.hrpartner.io/positions`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
employee | text | Specify the employee code to only see the position records for that particular employee.
department | text | Specify one or more department names (separated by commas) to only show employee position records within that department.
position | text | Specify the position name to list only records matching this position name.
comments | text | Return only position records with this partial text within the comments field.
remuneration_from, remuneration_to | number | Return position records where the remuneration is between these two figures (inclusive).
paylevel | text | Return position information where the pay level contains this text.
commence_date_from, commence_date_to | date (yyyy-mm-dd) | Return only position records which commenced between these two dates (inclusive).
completion_date_from, completion_date_to | date (yyyy-mm-dd) | Return only position records which completed between these two dates (inclusive).

### Examples

To get a list all position records in department "Finance":

`GET https://api.hrpartner.io/positions?department=Finance`

To find all position records which started in 2020 where the remuneration amount was between $50,000 and $60,000:

`GET https://api.hrpartner.io/positions?commence_date_from=2020-01-01&commence_date_to=2020-12-31&remuneration_from=50000&remuneration_to=60000`

To find all positions for "Delivery Truck Driver" then finished in March 2020:

`GET https://api.hrpartner.io/positions?position=Delivery Truck Driver&completion_date_from=2020-03-01&completion_date_to=2020-03-31`

### Attachments

If a position record includes attachments, they will be returned as an object array underneath the main position record.  The structure of this object is:

Parameter | Type | Description
--------- | ---- | -----------
description | text | The file name
url | text | The URL path to the file
size | number | The size of the file in bytes



## Renewables

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/renewables'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/renewables"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/renewables";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 3844,
    "renewable_type": "Class A Truck Licence",
    "description": "Multi segment lorry licence",
    "issue_date": "2015-10-01",
    "renewal_due": "2016-10-24",
    "comments": "New licence for a lorry. I mean a truck.",
    "employee": {
      "code": "BLENA",
      "first_names": "Arthur",
      "last_name": "Blenkinshop",
      "full_name": "Blenkinshop, Arthur",
      "department": "Sales"
    }
  },
  {
    "id": 3869,
    "renewable_type": "Drivers Licence",
    "description": "NT Drivers Licence",
    "issue_date": "2010-05-13",
    "renewal_due": "2016-05-13",
    "comments": "",
    "employee": {
      "code": "BURRS",
      "first_names": "Stacey",
      "last_name": "Burridge",
      "full_name": "Burridge, Stacey",
      "department": "Warehouse"
    }
    "attachments": [
      {
        "description": "S Burridge Licence.JPG",
        "url": "_5jGmaQIuOL3uqyP6MU22Q/attachments/cNh0JliuSEvD4zoMGOsQxA/S Burridge Licence.JPG",
        "size": 457352
      }
    ]
  },
  {
    "id": 3902,
    "renewable_type": "Forklift Licence",
    "description": "Class B Industrial Licence",
    "issue_date": "2015-11-01",
    "renewal_due": "2016-05-31",
    "comments": "",
    "employee": {
      "code": "HARVK",
      "first_names": "Kylie",
      "last_name": "Harvey",
      "full_name": "Harvey, Kylie",
      "department": "Customer Support"
    }
  }
]
```

The Renewables module contains the records for any renewable documents that have been recorded against your employee.

### HTTP Request

`GET https://api.hrpartner.io/renewables`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
employee | text | Specify the employee code to only see the renewable records for that particular employee.
department | text | Specify one or more department names (separated by commas) to only show employee renewable records within that department.
renewable_type | text | Specify the renewable type to list only records matching this type.
description | text | Return only renewable records with this partial text within the description field.
comments | text | Return only renewable records with this partial text within the comments field.
issue_date_from, issue_date_to | date (yyyy-mm-dd) | Return only renewable records which were issued between these two dates (inclusive).
renewal_date_from, renewal_date_to | date (yyyy-mm-dd) | Return only renewable records which are due to be renewed between these two dates (inclusive).

### Examples

To get a list all renewable records of the type "Drivers Licence" and department "Sales":

`GET https://api.hrpartner.io/renewables?renewable_type=Drivers Licence&department=Sales`

To find all renewable records that contain the word "forklift" in the description and due for renewal in March 2020:

`GET https://api.hrpartner.io/renewables?description=forklift&renewal_date_from=2020-03-01&renewal_date_to=2020-03-31`


### Attachments

If a renewable record includes attachments, they will be returned as an object array underneath the main renewable record.  The structure of this object is:

Parameter | Type | Description
--------- | ---- | -----------
description | text | The file name
url | text | The URL path to the file
size | number | The size of the file in bytes




## Reviews

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/reviews'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/reviews"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/reviews";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 5590,
    "review_type": "Three Month Review",
    "description": "3 month performance review",
    "review_date": "2015-10-23",
    "reviewer": "Judy Trant",
    "score": 6.0,
    "review_status": "Passed",
    "comments": "Arthur passed his 3 month review with flying colours.",
    "employee": {
      "code": "BLENA",
      "first_names": "Arthur",
      "last_name": "Blenkinshop",
      "full_name": "Blenkinshop, Arthur",
      "department": "Sales"
    }
  },
  {
    "id": 6030,
    "review_type": "One Month Review",
    "description": "Initial monthly review for Stacey",
    "review_date": "2015-07-29",
    "reviewer": "Dennis Burns",
    "score": 1.0,
    "review_status": "Failed",
    "comments": "",
    "employee": {
      "code": "BURRS",
      "first_names": "Stacey",
      "last_name": "Burridge",
      "full_name": "Burridge, Stacey",
      "department": "Warehouse"
    }
  },
  {
    "id": 6229,
    "review_type": "Annual Review",
    "description": "2015 Annual Review for Katrina",
    "review_date": "2015-10-01",
    "reviewer": "Tony Prentice",
    "score": 10.0,
    "review_status": "Passed",
    "comments": "Great review.  Katrina has met all her targets and is doing exceptionally well.",
    "employee": {
      "code": "BLACK",
      "first_names": "Katrina",
      "last_name": "Black",
      "full_name": "Black, Katrina",
      "department": "Warehouse"
    }
  },
  {
    "id": 6241,
    "review_type": "Three Month Review",
    "description": "Quarterly Goal Review",
    "review_date": "2015-11-07",
    "reviewer": "Stan Hullthorpe",
    "score": 9.5,
    "review_status": "Passed",
    "comments": "Kylie passed her 3 month review with flying colours.  She is quite positive about the upcoming training courses she has planned.",
    "employee": {
      "code": "HARVK",
      "first_names": "Kylie",
      "last_name": "Harvey",
      "full_name": "Harvey, Kylie",
      "department": "Customer Support"
    }
  }
]
```

The Reviews module contains the records for any performance reviews that have been recorded against your employee.

### HTTP Request

`GET https://api.hrpartner.io/reviews`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
employee | text | Specify the employee code to only see the reviews for that particular employee.
department | text | Specify one or more department names (separated by commas) to only show employee reviews within that department.
review_type | text | Specify the review type to list only reviews matching this type.
review_status | text | Specify the review status to list only reviews matching this status.
description | text | Return only review records with this partial text within the description field.
comments | text | Return only review records with this partial text within the comments field.
reviewer | text | Return only reviews with this partial text within the reviewer name field.
score_from, score_to | number | Return reviews where the score is between these two figures (inclusive).
review_date_from, review_date_to | date (yyyy-mm-dd) | Return only review records which fall between these two dates (inclusive).

### Examples

To get a list all reviews in department "Finance" for March 2020:

`GET https://api.hrpartner.io/reviews?department=Finance&review_date_from=2020-03-01&review_date_to=2020-03-31`

To find all "Monthly" reviews that scored between 5 and 10 points score:

`GET https://api.hrpartner.io/reviews?review_type=Monthly Review&score_from=5&score_to=10`

To find all reviews with a status of "Failed" in 2019 that were run by Mary Jones:

`GET https://api.hrpartner.io/reviews?review_status=Failed&reviewer=Mary Jones&review_date_from=2019-01-01&review_date_to=2019-12-31`

### Attachments

If a review record includes attachments, they will be returned as an object array underneath the main review record.  The structure of this object is:

Parameter | Type | Description
--------- | ---- | -----------
description | text | The file name
url | text | The URL path to the file
size | number | The size of the file in bytes




## Skills

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/skills'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/skills"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/skills";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 2125,
    "skill_name": "Word Processing",
    "skill_rating": "Very Good",
    "comments": "Knows how to do macros and other advanced stuff in Word. Can handle setting up a mail merge from an external database.",
    "employee": {
      "code": "BLENA",
      "first_names": "Arthur",
      "last_name": "Blenkinshop",
      "full_name": "Blenkinshop, Arthur",
      "department": "Sales"
    }
  },
  {
    "id": 2241,
    "skill_name": "Phone Manner",
    "skill_rating": "Excellent",
    "comments": "",
    "employee": {
      "code": "BURRS",
      "first_names": "Stacey",
      "last_name": "Burridge",
      "full_name": "Burridge, Stacey",
      "department": "Warehouse"
    }
  },
  {
    "id": 2275,
    "skill_name": "Word Processing",
    "skill_rating": "Good",
    "comments": "Stacey is pretty confident in creating and working in documents in Word.  Probably needs more instruction on how to use a large file system (on our server).",
    "employee": {
      "code": "BURRS",
      "first_names": "Stacey",
      "last_name": "Burridge",
      "full_name": "Burridge, Stacey",
      "department": "Warehouse"
    }
  },
  {
    "id": 2329,
    "skill_name": "Customer Relations",
    "skill_rating": "Excellent",
    "comments": "",
    "employee": {
      "code": "BLACK",
      "first_names": "Katrina",
      "last_name": "Black",
      "full_name": "Black, Katrina",
      "department": "Warehouse"
    }
  },
  {
    "id": 2388,
    "skill_name": "Operating Systems",
    "skill_rating": "Good",
    "comments": "",
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

The Skills module contains the records for any skills and abilities that have been recorded against your employee.

### HTTP Request

`GET https://api.hrpartner.io/skills`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
employee | text | Specify the employee code to only see the skill records for that particular employee.
department | text | Specify one or more department names (separated by commas) to only show employee skill records within that department.
skill_name | text | Return all skills which have this name.
skill_rating | text | Return all skills which have this rating.
skill_rating_from, skill_rating_to | text | Return all skills with a rating that falls between these two parameters.
comments | text | Return only skill records with this partial text within the comments field.

### Examples

To get a list all skills of type "Word Processing in department "Finance":

`GET https://api.hrpartner.io/skills?department=Finance&skill_name=Word Processing`

To find all skills with the name "Javascript Programming" that have a rating of 5 to 10:

`GET https://api.hrpartner.io/skills?skill_name=Javascript Programming&skill_rating_from=5&skill_rating_to=10`

To find all skills for "French Language" with a skill rating of "Fluent":

`GET https://api.hrpartner.io/skills?skill_name=French Language&skill_rating=Fluent`

### Attachments

(Please note that Skill ratings do not have attachments)





## Training

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/training'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/training"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/training";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 3110,
    "training_type": "First Aid",
    "course_name": "First Aid Certificate training (Stage 1)",
    "institution": "St Johns Ambulance",
    "commence_date": "2015-10-01",
    "completion_date": "2015-10-03",
    "training_status": "Completed",
    "cost": 70.0,
    "reimbursement": 0.0,
    "comments": "",
    "employee": {
      "code": "KENNA",
      "first_names": "Arlene",
      "last_name": "Kennedy",
      "full_name": "Kennedy, Arlene",
      "department": "Administration"
    }
  },
  {
    "id": 3212,
    "training_type": "First Aid",
    "course_name": "First Aid Certificate training (Grade 2)",
    "institution": "Internal",
    "commence_date": "2015-08-05",
    "completion_date": "2015-08-13",
    "training_status": "Completed",
    "cost": 100.0,
    "reimbursement": 50.0,
    "comments": "Bella did the internal training course.",
    "employee": {
      "code": "LANEB",
      "first_names": "Bella",
      "last_name": "Lane",
      "full_name": "Lane, Bella",
      "department": "Personnel"
    }
  },
  {
    "id": 3345,
    "training_type": "Induction",
    "course_name": "Company Induction 101",
    "institution": "Internal",
    "commence_date": "2015-10-01",
    "completion_date": "2015-10-02",
    "training_status": "Completed",
    "cost": 80.0,
    "reimbursement": 0.0,
    "comments": "Bella did really well with this course.",
    "employee": {
      "code": "LANEB",
      "first_names": "Bella",
      "last_name": "Lane",
      "full_name": "Lane, Bella",
      "department": "Personnel"
    },
    "attachments": [
      {
        "description": "PST.png",
        "url": "_5jGmaQIuOL3uqyP6MU22Q/attachments/vcpkvR6aosbrUg2LhIljYA/PST.png",
        "size": 6020
      },
      {
        "description": "Certificate.png",
        "url": "_5jGmaQIuOL3uqyP6MU22Q/attachments/vcpkvR6aosbrUg2LhIljYA/Certificate.png",
        "size": 7611
      }
    ]
  },
  {
    "id": 3487,
    "training_type": "First Aid",
    "course_name": "First Aid Certificate",
    "institution": "St Johns Ambulance",
    "commence_date": "2015-11-05",
    "completion_date": "2015-11-09",
    "training_status": "Completed",
    "cost": 90.0,
    "reimbursement": 90.0,
    "comments": "",
    "employee": {
      "code": "HARVK",
      "first_names": "Kylie",
      "last_name": "Harvey",
      "full_name": "Harvey, Kylie",
      "department": "Customer Support"
    }
  },
]
```

The Training module contains the records for any internal or extra training courses that have been recorded against your employee.

### HTTP Request

`GET https://api.hrpartner.io/training`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
employee | text | Specify the employee code to only see the training records for that particular employee.
department | text | Specify one or more department names (separated by commas) to only show employee training records within that department.
training_type | text | Specify the training type to list only entries matching this type.
training_status | text | Specify the training status to list only entries matching this status.
course_name | text | Return only records with this partial text in the course name field.
institution | text | Return only records that has this partial text in the course intitution field.
comments | text | Return only training records with this partial text within the comments field.
cost_from, cost_to | number | Return training records where the cost was between these two figures (inclusive).
reimbursement_from, reimbursement_to | number | Return training records where the reimbursement to the employee was between these two figures (inclusive).
commence_date_from, commence_date_to | date (yyyy-mm-dd) | Return only training records which commenced between these two dates (inclusive).
completion_date_from, completion_date_to | date (yyyy-mm-dd) | Return only training records which completed between these two dates (inclusive).

### Examples

To get a list all training type "First Aid" in department "Finance":

`GET https://api.hrpartner.io/training?department=Finance&training_type=First Aid`

To find all training that cost between $50 and $100 that was run in March 2020:

`GET https://api.hrpartner.io/training?cost_from=50&cost_to=100&commence_date_from=2020-03-01&commence_date_to=2020-03-31`

To find all training with a status of "Passed" in 2019 where the employees were reimbursed at least $100:

`GET https://api.hrpartner.io/training?training_status=Passed&reimbursement_from=100&reimbursement_to=99999`

### Attachments

If a training record includes attachments, they will be returned as an object array underneath the main training record.  The structure of this object is:

Parameter | Type | Description
--------- | ---- | -----------
description | text | The file name
url | text | The URL path to the file
size | number | The size of the file in bytes




# Lookups

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/lookups/absence_reasons'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/lookups/absence_reasons"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/lookups/absence_reasons";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 2051,
    "name": "Annual Leave"
  },
  {
    "id": 2589,
    "name": "Bereavement Leave"
  },
  {
    "id": 2664,
    "name": "PTO"
  },
  {
    "id": 2878,
    "name": "Sick Leave"
  },
  {
    "id": 3012,
    "name": "Study Leave"
  }
]
```

This endpoint retrieves information from any of the lookup files that are used in the drop downs within HR Partner.

### HTTP Request

`GET https://api.hrpartner.io/lookups/{lookupName}`

### Lookup Names

Name | Description
---- | -----------
absence_reasons | Leave/Time Off/Absence types
absence_statuses | Leave/Time Off/Absence statuses
asset_types | Asset types
benefit_types | Benefit package type
benefit_statuses | Benefit package statuses
departments | Departments used within HR Partner
dependent_types | Dependent/Next of Kin type
education_types | Prior education types
education_statuses | Prior education statuses
employment_statuses | Employment Status (e.g. Full Time, Part Time etc.)
genders | Gender list (if extended gender identities turned on in company options)
grievance_types | Grievance/Complaints/Harrassment types
grievance_statuses | Grievance/Complaints/Harrassment statuses
interview_types | Interview/Meeting types
locations | Locations used within HR Partner
pay_levels | Pay levels used in Position records
positions | Position/Job descriptions within HR Partner
renewable_types | Renewable document types
renewable_statuses | Renewable document statuses
review_types | Performance review types
review_statuses | Performance review statuses
skill_names | Skill names
skill_ratings | Skill ratings
tags | Tags used within HR Partner
training_types | Training types
training_statuses | Training statuses

<aside class="notice">Please note that currently, you can only read from these lookup files, but not make any changes to them via the API.</aside>

### Examples

To get a list of all asset types:

`GET https://api.hrpartner.io/lookups/asset_types`

To get a list of all position descriptions in HR Partner:

`GET https://api.hrpartner.io/lookups/positions`

To get a list of all tags used in HR Partner:

`GET https://api.hrpartner.io/lookups/tags`

<aside class="success"><strong>Tip:</strong> Use the lookup calls to get a list of valid types and statuses that you can use in the filter parameters when calling other information such as employee training records or assets out on loan etc.</aside>


# Reminders

## Get All Reminders

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/reminders'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/reminders"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/reminders";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 3701,
    "description": "iPhone 6",
    "module": "asset",
    "module_id": 17,
    "remind_at": "2015-10-31T22:45:00+00:00",
    "send_notification": false,
    "notification_sent": false,
    "active": true,
    "set_by": {
      "name": "Deanna Burwood",
      "email": "deanne@mailinator.com"
    },
    "employee": {
      "code": "LANDC",
      "first_names": "Clinton",
      "last_name": "Landry",
      "full_name": "Landry, Clinton",
      "department": "Production"
    }
  },
  {
    "id": 3752,
    "description": "iPhone 3GS",
    "module": "asset",
    "module_id": 16,
    "remind_at": "2015-11-01T22:45:00+00:00",
    "send_notification": true,
    "notification_sent": false,
    "active": false,
    "set_by": {
      "name": "Barbara McBain",
      "email": "barbara@mailinator.com"
    },
    "employee": {
      "code": "BUTTJ",
      "first_names": "James",
      "last_name": "Butterworth",
      "full_name": "Butterworth, James",
      "department": "Production"
    }
  },
  {
    "id": 3796,
    "description": "Took a day off",
    "module": "absence",
    "module_id": 18,
    "remind_at": "2015-11-01T22:45:00+00:00",
    "send_notification": true,
    "notification_sent": false,
    "active": true,
    "set_by": {
      "name": "Deanne Burwood",
      "email": "deanna@mailinator.com"
    },
    "employee": {
      "code": "GARCH",
      "first_names": "Hilda",
      "last_name": "Garcia",
      "full_name": "Garcia, Hilda",
      "department": "Sales"
    }
  },
  {
    "id": 3822,
    "description": "Speak to James about his request for a promotion",
    "module": "note",
    "module_id": 36,
    "remind_at": "2015-11-01T22:45:00+00:00",
    "send_notification": true,
    "notification_sent": false,
    "active": false,
    "set_by": {
      "name": "Barbara McBain",
      "email": "barbara@mailinator.com"
    },
    "employee": {
      "code": "BUTTJ",
      "first_names": "James",
      "last_name": "Butterworth",
      "full_name": "Butterworth, James",
      "department": "Production"
    }
  },
  {
    "id": 3847,
    "description": "Taken a day off!",
    "module": "absence",
    "module_id": 17,
    "remind_at": "2015-11-02T22:45:00+00:00",
    "send_notification": true,
    "notification_sent": false,
    "active": false,
    "set_by": {
      "name": "Barbara McBain",
      "email": "barbara@mailinator.com"
    },
    "employee": {
      "code": "BUTTJ",
      "first_names": "James",
      "last_name": "Butterworth",
      "full_name": "Butterworth, James",
      "department": "Production"
    }
  }
]
```

This endpoint retrieves all reminders that are currently in the system.

### HTTP Request

`GET https://api.hrpartner.io/reminders`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
employee | text | Return only reminders for employees with this employee code.
department | text | Specify one or more department names (separated by commas) to only show reminders within that department.
user | text (email) | Return reminders where the admin user who is responsible for them has this email address.
module | text | Return reminders which belong to this particular [module](#module) only.
send_notification | true/false | Return reminders that have the `send_notification` flag set this way (true or false).
notification_sent | true/false | Select reminders that have the `notification_sent` flag set this way (true or false).
active | true/false | Return reminders where the `active flag` is set this way (true or false).


### Examples

To get a list of all reminders for employee code A12345:

`GET https://api.hrpartner.io/reminders?employee=A12345`

To get all reminders sent by joe@acme.com within the "Finance" department:

`GET https://api.hrpartner.io/reminders?user=joe@acme.com&department=Finance`

To get all reminders for the "training" module that have not been sent out yet:

`GET https://api.hrpartner.io/reminders?module=training&notification_sent=false`


## Get A Specific Reminder

```ruby
require 'rest-client'

header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}
endpoint = 'https://api.hrpartner.io/reminder/'
reminderid = '3804'

result = RestClient.get(endpoint + reminderid, header)

puts result
```

```shell
curl "https://api.hrpartner.io/reminder/3804"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};
var endpoint = "https://api.hrpartner.io/reminder/";
var reminderid = "3804"

client.get(endpoint + reminderid, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this:

```json
{
  "id": 3804,
  "description": "iPhone 6",
  "module": "asset",
  "module_id": 17,
  "remind_at": "2015-10-31T22:45:00+00:00",
  "send_notification": false,
  "notification_sent": false,
  "active": true,
  "set_by": {
    "name": "Deanna Burwood",
    "email": "deanna@mailinator.com"
  },
  "employee": {
    "code": "LANDC",
    "first_names": "Clinton",
    "last_name": "Landry",
    "full_name": "Landry, Clinton",
    "department": "Production"
  }
}
```

This endpoint retrieves a single reminder from the system using the **_Reminder ID_**.

### HTTP Request

`GET https://api.hrpartner.io/reminder/{reminderID}`

This call will return a single reminder based on the unique reminder ID from HR Partner.


<aside class="notice">Tip: You can use the <code>GET /reminders</code> call to get a list of all reminders, then extract the <em>ID</em> field from the results to fetch individual reminders.</aside>


## Update A Reminder

```ruby
require 'rest-client'

# Update reminder description and notification
postbody = {
  "id": 3804,
  "description": "Return the iPhone 6 to Steve",
  "send_notification": true,
  "notification_sent": false,
  "active": true
}

header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d', :body => postbody}
endpoint = 'https://api.hrpartner.io/reminder/'
reminderid = '3804'

result = RestClient.post(endpoint + reminderid, header)

puts result
```

```shell
curl "https://api.hrpartner.io/reminder/3804"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
  -H "Content-Type: application/json"
  -X POST
  -d '{"id": 3804, "description": "Return the iPhone 6 to Steve", "send_notification": true, "notification_sent": false, "active": true}'
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();

// Update Arthur's record with tax number, update custom fields with new salary and work times, add contractor tag, change mobile number and add new email
var postbody = postbody = {
  "id": 3804,
  "description": "Return the iPhone 6 to Steve",
  "send_notification": true,
  "notification_sent": false,
  "active": true
}

var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}, body: postbody};
var endpoint = "https://api.hrpartner.io/reminder/";
var reminderid = "3804"

client.post(endpoint + reminderid, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this:

```json
{
  "id": 3804,
  "description": "Return the iPhone 6 to Steve",
  "module": "asset",
  "module_id": 17,
  "remind_at": "2015-10-31T22:45:00+00:00",
  "send_notification": true,
  "notification_sent": false,
  "active": true,
  "set_by": {
    "name": "Deanna Burwood",
    "email": "deanna@mailinator.com"
  },
  "employee": {
    "code": "LANDC",
    "first_names": "Clinton",
    "last_name": "Landry",
    "full_name": "Landry, Clinton",
    "department": "Production"
  }
}
```


This endpoint will update _certain fields_ on a reminder.

### HTTP Request

`POST https://api.hrpartner.io/reminder/{reminderID}`

A successful POST will return a reminder object (see the `GET /reminder` call above) upon successful modification.

<aside class="warning">
  <strong>Note:</strong> You CANNOT change the employee or the admin user details on a reminder, nor the actual date of the reminder.  The only things you can change at this point in time is the description, and the flags on the reminder.
</aside>

### POST Body

The JSON packet that can be POSTed to the endpoint is a subset of the JSON that you receive from the GET call to the `/reminder` endpoint.

Parameter | Type | Description
--------- | ---- | -----------
id<sup>*</sup> | number | The reminder id
description | text | The description of the reminder
send_notification | true/false | Flag whether to send a notification to the admin user
notification_sent | true/false | Flag whether the notification has been sent to the admin user
active | true/false | Flag whether the reminder is active in HR Partner


_<sup>*</sup> - Mandatory (required) field_


Please note that the reminder id is also required in the POST body as well as the URL for added verification and security.

## Delete A Reminder

```ruby
require 'rest-client'

# Update reminder description and notification
postbody = {
  "id": 3804,
  "description": "Return the iPhone 6 to Steve",
  "send_notification": true,
  "notification_sent": false,
  "active": true
}

header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d', :body => postbody}
endpoint = 'https://api.hrpartner.io/reminder/'
reminderid = '3804'

result = RestClient.delete(endpoint + reminderid, header)

puts result
```

```shell
curl "https://api.hrpartner.io/reminder/3804"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
  -H "Content-Type: application/json"
  -X DELETE
  -d '{"id": 3804, "description": "Return the iPhone 6 to Steve", "send_notification": true, "notification_sent": false, "active": true}'
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();

// Update Arthur's record with tax number, update custom fields with new salary and work times, add contractor tag, change mobile number and add new email
var postbody = postbody = {
  "id": 3804,
  "description": "Return the iPhone 6 to Steve",
  "send_notification": true,
  "notification_sent": false,
  "active": true
}

var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}, body: postbody};
var endpoint = "https://api.hrpartner.io/reminder/";
var reminderid = "3804"

client.delete(endpoint + reminderid, info, function(data, response) {
  console.log(response;
});
```

> The above command returns HTTP 200 if the command completed successfully


This endpoint will delete a reminder completely from HR Partner.


### HTTP Request

`DELETE https://api.hrpartner.io/reminder/{reminderID}`

A successful DELETE will return HTTP code '200' upon successful deletion.

<aside class="warning">
  <strong>Note:</strong> This will delete a reminder entirely from HR Partner.  There is no 'undo' function for this so please be sure that you wish to remove a reminder.
</aside>




# Recruitment


## Get All Job Listings

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/jobs'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/jobs"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/jobs";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": "forklift-driver-oz0H",
    "title": "Forklift Driver",
    "summary": "We need an enthusiastic person to drive the forklift in our warehouse.",
    "publish_at": "2020-01-01",
    "unpublish_at": "2020-02-15",
    "city": "Sydney",
    "state": "NSW",
    "country": "Australia",
    "postcode": "2040",
    "department": "Warehouse",
    "location": "Sydney Branch",
    "position": "Driver",
    "employment_status": "Casual",
    "is_active": true,
    "view_count": 2206
  },
  {
    "id": "warehouse-manager--distribution--2zGd",
    "title": "Warehouse Manager (Distribution)",
    "summary": "Your new company, a leading Australian retailer, is experiencing rapid growth and as a result requires an experienced Assistant Warehouse Manager to facilitate and support the Warehouse Operations in this extremely exciting time for the business. Based in South Melbourne, just a short journey from the city, this established organisation with a strong market reputation is extremely ambitious; this is reflected in their success, with nearly 200 stores nationwide.",
    "publish_at": "2019-10-26",
    "unpublish_at": "2020-02-15",
    "city": "Tokyo",
    "state": "",
    "country": "Japan",
    "postcode": "K405",
    "department": "Warehouse",
    "location": "Asia/Pacific",
    "position": "Warehouse Manager",
    "employment_status": "Full Time",
    "is_active": false,
    "view_count": 3511
  },
  {
    "id": "senior-javascript-developer-kj",
    "title": "Senior Javascript Developer",
    "summary": "As a Front-end Developer with Acme Software you will use your exceptional web development skills and experiences to develop responsive websites and web applications. As a member of our world-class agency you will work on innovative and inspired work across a variety of clients.",
    "publish_at": "2020-03-13",
    "unpublish_at": "2020-05-20",
    "city": "Sydney",
    "state": "NSW",
    "country": "Australia",
    "postcode": "2310",
    "department": "Production",
    "location": "Sydney Branch",
    "position": "Programmer",
    "employment_status": "Full Time",
    "is_active": true,
    "view_count": 14612
  },
  {
    "id": "warehouse-assistant-lk",
    "title": "Warehouse Assistant",
    "summary": "We need a warehouse assistant to help our supervisors to improve their loading and searching ability.  We are really looking for an enthusiastic, young person who doesn't mind a little bit of hard work.  This is a casual position with an 'on call' working time basis.",
    "publish_at": "2020-05-10",
    "unpublish_at": "2020-07-10",
    "city": "Singapore",
    "state": "N/A",
    "country": "Singapore",
    "postcode": "5000",
    "department": "Warehouse",
    "location": "Asica/Pacific",
    "position": "Packer",
    "employment_status": "Casual",
    "is_active": true,
    "view_count": 1918
  }
]
```

This endpoint retrieves all job listings that are currently in the system.

### HTTP Request

`GET https://api.hrpartner.io/jobs`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
search | text | Return only jobs with this text string in either the title, summary or text/web content
department | text | Returns jobs that are allocated to this department name
location | text | Returns jobs that are in this location name
position | text | Returns jobs with this position title
employment_status | text | Returns jobs for this employment status name (e.g. Full Time, Part Time etc.)
publish_at_from, publish_at_to | date (yyyy-mm-dd) | Date range that the job listing was set to be published
unpublish_date_from, unpublish_date_to | date (yyyy-mm-dd) | Date range that the job listing was set to be un-published
is_active | true/false | Flag for whether job listings marked active will be returned
publish_on_internet | true/false | Flag whether to return job listings marked as being show on the internet
allow_online_applications | true/false | Flag whether to return jobs where candidates can make online applications
allow_uploads | true/false | Flag whether to return job listings that allow candidate to upload files to
notify_new_application | true/false | Flag whether to return listings that will notify the admin when a job applications is entered
response_email | text | Returns jobs with this email address set as the address that all responses will be sent to


### Examples

To get a list of all job listings for the 'Warehouse' department:

`GET https://api.hrpartner.io/jobs?department=Warehouse`

To get a list of all job listings that contain the word 'driver' in the title, summary, text content or web content:

`GET https://api.hrpartner.io/jobs?search=driver`

To get all job listings published in the first quarter of 2020:

`GET https://api.hrpartner.io/jobs?publish_at_from=2020-01-01&publish_at_to=2020-03-31`

To get all job listings in the 'New York' and 'Boston' locations that are still active:

`GET https://api.hrpartner.io/jobs?location=New York,Boston&is_active=true`

To get all job listings that are published on the internet and that have 'hr@company.com' as the email to respond to:

`GET https://api.hrpartner.io/jobs?publish_on_internet=true&response_email=hr@mycompany.com`


## Get A Specific Job Listing

```ruby
require 'rest-client'

header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}
endpoint = 'https://api.hrpartner.io/job/'
jobid = 'forklift-driver-oz0H'

result = RestClient.get(endpoint + jobid, header)
puts result

```

```shell
curl "https://api.hrpartner.io/job/forklift-driver-oz0H"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"

```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};
var endpoint = "https://api.hrpartner.io/job/";
var jobid = "forklift-driver-oz0H"

client.get(endpoint + jobid, info, function(data, response) {
  console.log(response;
});

```

> The above command returns JSON structured like this:

```json
{
  "id": "forklift-driver-oz0H",
  "title": "Forklift Driver",
  "summary": "We need an enthusiastic person to drive the forklift in our warehouse.",
  "publish_at": "2020-01-01",
  "unpublish_at": "2020-02-15",
  "department": "Warehouse",
  "location": "Sydney Branch",
  "position": "Driver",
  "employment_status": "Casual",
  "text_content": "...text content of job goes here (long)...",
  "web_content": "<p>... HTML content of job goes here (very long)...</p>",
  "city": "Sydney",
  "state": "NSW",
  "country": "Australia",
  "postcode": "2040",
  "is_active": true,
  "publish_on_internet": true,
  "allow_online_application": true,
  "notify_new_application": false,
  "allow_uploads": true,
  "mandatory_uploads": false,
  "view_count": 22,
  "response_email": "hr@mailinator.com",
  "selection_panel": [
    {
      "type": "user",
      "name": "Jane Smithson",
      "email": "janesmithson@mailinator.com"
    },
    {
      "type": "user",
      "name": "Jimmy Tango",
      "email": "thetango@mailinator.com"
    },
    {
      "type": "employee",
      "name": "Peter Stephenson",
      "email": "pstephenson@mailinator.com"
    },
    {
      "type": "employee",
      "name": "Michale Fuller",
      "email": "mfuller@mailinator.com"
    }
  ],
  "custom_form": {
    "name": "Driver Appplication Form",
    "layout": [
      {
        "type": "paragraph",
        "subtype": "p",
        "label": "We need to have at least two references from you before we can proceed with your application."
      },
      {
        "type": "text",
        "required": true,
        "label": "Reference #1 Name",
        "className": "form-control",
        "name": "reference-1-name",
        "subtype": "text"
      },
      {
        "type": "text",
        "required": true,
        "label": "Reference #1 Contact",
        "className": "form-control",
        "name": "reference-1-contact",
        "subtype": "text"
      },
      {
        "type": "text",
        "label": "Reference #2 Name",
        "className": "form-control",
        "name": "reference-2-name",
        "subtype": "text"
      },
      {
        "type": "text",
        "label": "Reference #2 Contact",
        "className": "form-control",
        "name": "reference-2-contact",
        "subtype": "text"
      },
      {
        "type": "checkbox-group",
        "label": "Drivers Licence",
        "name": "drivers-licence",
        "values": [
          {
            "label": "Car Licence",
            "value": "car",
            "selected": true
          },
          {
            "label": "Small Van Licence",
            "value": "van"
          },
          {
            "label": "Truck Licence",
            "value": "truck"
          },
          {
            "label": "Bus Licence",
            "value": "bus"
          },
          {
            "label": "Heavy Vehicle",
            "value": "heavy"
          }
        ]
      },
      {
        "type": "radio-group",
        "label": "Do you have an international licence?",
        "name": "international-licence",
        "values": [
          {
            "label": "Yes",
            "value": "yes",
            "selected": true
          },
          {
            "label": "No",
            "value": "no"
          },
          {
            "label": "Maybe",
            "value": "maybe"
          }
        ]
      },
      {
        "type": "date",
        "label": "Date Licence Issued",
        "className": "form-control",
        "name": "licence-issue-date"
      },
      {
        "type": "textarea",
        "label": "Reason for Applying",
        "placeholder": "Tell us why you want to apply (up to 1000 characters)",
        "className": "form-control",
        "name": "application-reason",
        "subtype": "textarea",
        "maxlength": "1000",
        "rows": "5"
      }
    ]
  },
  "scorecard": {
    "name": "Warehouse Worker Scoring",
    "items": [
      "Initiative",
      "Attitude",
      "Safety Awareness",
      "Leadership",
      "Motivation"
    ]
  },
  "stages": {
    "name": "Warehouse Job Stages",
    "items": [
      "Applied",
      "Phone Screening",
      "Interview",
      "Reference Check",
      "Job Offer",
      "Rejected"
    ]
  }
}
```

This endpoint retrieves a single job listing from the system using the **_Job ID_**.

### HTTP Request

`GET https://api.hrpartner.io/job/{jobID}`

This call will return a single job listing based on the unique _Job ID_ from HR Partner.

<aside class="notice">Tip: You can use the <code>GET /jobs</code> call to get a list of all jobs, then extract the <em>ID</em> field from the results to fetch individual job listings.</aside>



## Get All Applicants

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/applicants'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/applicants"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/applicants";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": "waLHyCLupvwXKM2VfPy47g",
    "first_names": "Susan",
    "last_name": "Anthony",
    "full_name": "Anthony, Susan",
    "email": "susananthony@mailinator.com"
  },
  {
    "id": "P-vRRK51Cszbad7PVAlYog",
    "first_names": "Annie",
    "last_name": "Arbiter",
    "full_name": "Arbiter, Annie",
    "email": "annie@mailinator.com"
  },
  {
    "id": "1rno4l5p3ciTyGziZcqF8g",
    "first_names": "Felix",
    "last_name": "Baumgartner",
    "full_name": "Baumgartner, Felix",
    "email": "flyingfelix@mailinator.com"
  },
  {
    "id": "c_RNAxMend-iU02lrCbVgQ",
    "first_names": "John",
    "last_name": "Bollinger",
    "full_name": "Bollinger, John",
    "email": "jbollinger@mailinator.com"
  },
  {
    "id": "JXI026hdUl1K9LxG6_3JPQ",
    "first_names": "Geoff",
    "last_name": "Bouncer",
    "full_name": "Bouncer, Geoff",
    "email": "geoffbouncer@myemail.test"
  },
  {
    "id": "34XiVeAOJ-hz6agE15VvIQ",
    "first_names": "Jason",
    "last_name": "Bourne",
    "full_name": "Bourne, Jason",
    "email": "jasonbourne@mailinator.com"
  }
]
```

This endpoint retrieves all applicants (candidates for job listings) that are currently in the system.

### HTTP Request

`GET https://api.hrpartner.io/applicants`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
search | text | Return only applicants with this text string in either their first name, last name or email.


### Examples

To get a list of all applicants with 'Smith' in their name:

`GET https://api.hrpartner.io/applicants?search=Smith`

To get all applicants with a Gmail address:

`GET https://api.hrpartner.io/applicants?search=@gmail.com`



## Get A Specific Applicant

```ruby
require 'rest-client'

header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}
endpoint = 'https://api.hrpartner.io/applicant/'
applicantid = 'waLHyCLupvwXKM2VfPy47g'

result = RestClient.get(endpoint + applicantid, header)
puts result

# alternative - use email address for the ID

applicantid = 'susananthony@mailinator.com'

result = RestClient.get(endpoint + applicantid, header)
puts result

```

```shell
curl "https://api.hrpartner.io/applicant/waLHyCLupvwXKM2VfPy47g"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"

curl "https://api.hrpartner.io/applicant/susananthony@mailinator.com"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};
var endpoint = "https://api.hrpartner.io/applicant/";
var applicantid = "waLHyCLupvwXKM2VfPy47g"

client.get(endpoint + applicantid, info, function(data, response) {
  console.log(response;
});

// alternative - user email address for the ID
var applicantid = "susananthony@mailinator.com"

client.get(endpoint + applicantid, info, function(data, response) {
  console.log(response;
});


```

> The above command returns JSON structured like this:

```json
{
  "id": "waLHyCLupvwXKM2VfPy47g",
  "first_names": "Susan",
  "last_name": "Anthony",
  "full_name": "Anthony, Susan",
  "email": "susananthony@mailinator.com",
  "job_applications": [
    {
      "id": "forklift-driver-o0",
      "name": "Forklift Driver",
      "stage": "Job Offer",
      "submitted_at": "2017-05-28T09:17:02+00:00",
      "is_closed": true,
      "is_active": false,
      "is_flagged": false,
      "is_archived": false,
      "is_hired": true,
      "is_read": true,
      "source": "Entered by Andy Bernard",
      "total_score": 3.0
    },
    {
      "id": "senior-javascript-developer-kj",
      "name": "Senior Javascript Developer",
      "stage": "Applied",
      "submitted_at": "2017-06-08T23:54:32+00:00",
      "is_closed": false,
      "is_active": true,
      "is_flagged": false,
      "is_archived": false,
      "is_hired": false,
      "is_read": true,
      "source": "Added to Application by Steve Cooper",
      "total_score": 4.0
    }
  ]
}
```

This endpoint retrieves a single applicant from the system using the **_Applicant ID_**.  It will also return any job applications (if any) that this applicant has created in the system.

### HTTP Request

`GET https://api.hrpartner.io/applicant/{applicantID}`

This call will return a single applicant based on the unique _Applicant ID_ from HR Partner.

Note: The Applicant ID can be either the unique ID string that you obtain from the applicants list above, or else you can use the applicant's email address.  Email addresses are also treated as the unique identifier for applicants within HR Partner.


<aside class="notice">Tip: You can use the <code>GET /applicants</code> call to get a list of all applicants, then extract the <em>ID</em> field from the results to fetch individual applicants.  Or else just use their email address as the ID, which you can also get from the above call.</aside>


## Add or Update An Applicant

```ruby
require 'rest-client'

# Update applicant details and application
postbody = {
  "first_names": "Peter",
  "last_name": "Kensington",
  "email": "kensingtonpete@mailinator.com",
  "job_applications": [
    {
      "id": "another-test-job-pg",
      "stage": "First Interview"
    }
  ]
}

header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d', :body => postbody}
endpoint = 'https://api.hrpartner.io/applicant/'

result = RestClient.post(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/applicant"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
  -H "Content-Type: application/json"
  -X POST
  -d '{"first_names": "Peter", "last_name": "Kensington", "email": "kensingtonpete@mailinator.com", "job_applications": [{"id": "another-test-job-pg", "stage": "First Interview"}]}'
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();

// Update Arthur's record with tax number, update custom fields with new salary and work times, add contractor tag, change mobile number and add new email
var postbody = postbody = {
  "first_names": "Peter",
  "last_name": "Kensington",
  "email": "kensingtonpete@mailinator.com",
  "job_applications": [
    {
      "id": "another-test-job-pg",
      "stage": "First Interview"
    }
  ]
}

var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}, body: postbody};
var endpoint = "https://api.hrpartner.io/applicant/";

client.post(endpoint, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this:

```json
{
  "id": "k0Gx8fvn1eBDDS3P8uqVXA",
  "first_names": "Peter",
  "last_name": "Kensington",
  "full_name": "Kensington, Peter",
  "email": "kensingtonpete@mailinator.com",
  "job_applications": [
    {
      "id": "another-test-job-pg",
      "name": "Another Test Job",
      "stage": "First Interview",
      "submitted_at": "2020-05-22T09:31:15+00:00",
      "is_closed": false,
      "is_active": true,
      "is_flagged": false,
      "is_archived": false,
      "is_hired": false,
      "is_read": false,
      "source": "Entered via API",
      "total_score": 0.0
    }
  ]
}
```


This endpoint will update _certain fields_ for an applicant and/or their job application.

### HTTP Request

`POST https://api.hrpartner.io/applicant`

A successful POST will return a applicant object (see the `GET /applicant` call above) upon successful modification.

<aside class="warning">
  <strong>Note:</strong> This call will create the applicant if the email address does not already exist in the system, or it will update the details of the applicant if the email address already exists.
</aside>

### POST Body

The JSON packet that can be POSTed to the endpoint is a subset of the JSON that you receive from the GET call to the `/applicant` endpoint.

Parameter | Type | Description
--------- | ---- | -----------
email<sup>*</sup> | text | The applicant email address
first_names | text | The applicants first name
last_name | text| The applicants last name
job_applications | array | An array of one or more jobs that the applicants is applying for

The following describes the fields in the `job_applications` array:

Parameter | Type | Description
--------- | ---- | -----------
id<sup>*</sup> | text | The job listing unique slug (see `/job_listing` endpoint)
stage | text | The stage of the job application pipeline that the candidate is in (must be an existing stage name)


_<sup>*</sup> - Mandatory (required) field_

<aside class="info">
  <strong>Note:</strong> You can change the Stage of the pipeline that the applicant is in by specifying an existing applicant email and name in the first part of the POST body, then specifying the job listing slug and the Stage name in the second part (the `job_applications` array).  Specifying a different Stage name will just move the applicant into that stage immediately.
</aside>



## Get All Applications

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/applications/'
jobid = 'delivery-truck-driver-oh6P'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint + jobid, header)

puts result
```

```shell
curl "https://api.hrpartner.io/applications/delivery-truck-driver-oh6P"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/applications";
var jobid = "delivery-truck-driver-oh6P";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint + jobid, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 7344,
    "job_id": "delivery-truck-driver-oh6P",
    "title": "Warehouse Delivery Truck Driver Wanted",
    "applicant_id": "waLHyCLupvwXKM2VfPy47g",
    "first_names": "Susan",
    "last_name": "Anthony",
    "email": "susananthony@mailinator.com",
    "stage": "Applied",
    "source": "Entered by Arthur Dent",
    "submitted_at": "2020-05-28T09:17:02+00:00",
    "is_flagged": false,
    "is_archived": false,
    "is_hired": false,
    "is_read": true
  },
  {
    "id": 7396,
    "job_id": "delivery-truck-driver-oh6P",
    "title": "Warehouse Delivery Truck Driver Wanted",
    "applicant_id": "qu0_94N0nd9pDtvfWuYWVQ",
    "first_names": "Johnny",
    "last_name": "Strange",
    "email": "johnnystrange@mailinator.com",
    "stage": "Interview",
    "source": "[Job Portal] http://mycompany.hrpartner.io/jobs",
    "submitted_at": "2020-05-28T09:18:00+00:00",
    "is_flagged": true,
    "is_archived": false,
    "is_hired": false,
    "is_read": true
  },
  {
    "id": 8029,
    "job_id": "delivery-truck-driver-oh6P",
    "title": "Warehouse Delivery Truck Driver Wanted",
    "applicant_id": "8ejwdwiytKm9SjqwZ2LJUg",
    "first_names": "Janine",
    "last_name": "Rogers",
    "email": "janinerogers@mailinator.com",
    "stage": "Interview",
    "source": "Entered by Arthur Dent",
    "submitted_at": "2020-05-28T09:29:25+00:00",
    "is_flagged": false,
    "is_archived": false,
    "is_hired": false,
    "is_read": false
  }
]
```

This endpoint retrieves all job applications for a particular job listing that are currently in the system.

### HTTP Request

`GET https://api.hrpartner.io/applications/{jobID}`

This call will retrieve all job applications for the job listing identified in the _Job ID_ parameter.  Please note that you will have to specify a job listing.  It is not possible to get a common list of ALL job applications in the system via the API.

The _Job ID_ can be retrieved by calling the `GET /jobs` endpoint as described elsewhere in this documentation.

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
source | text | Return only applications with this text string in the source field.
stage | text | Return only applications that are in this stage specified.
submitted_at_from, submitted_at_to | date (yyyy-mm-dd) | Fetch only applications submitted between these two dates.
is_flagged | true/false | Return only applications which have been flagged.
is_archived | true/false | Return applications which have been archived.
is_hired | true/false | Return applications only for candidates who have been hired within the system.
is_read | true/false | Useful for picking out applications that have or have not been opened in HR Partner yet.


### Examples

Note: All these examples assume you are pulling applications from the `delivery-truck-driver-oh6P` job listing ID.

To get a list of all applications that have been sourced from Indeed.com:

`GET https://api.hrpartner.io/applications/delivery-truck-driver-oh6P?source=Indeed`

To get all applications which are in the 'Second Interview' stage:

`GET https://api.hrpartner.io/applicants/delivery-truck-driver-oh6P?stage=Second Interview`

To get all applications which were submitted in March 2020 and have not been read or viewed in HR Partner yet:

`GET https://api.hrpartner.io/applicants/delivery-truck-driver-oh6P?submitted_at_from=2020-03-01&submitted_at_to=2020-03-31&is_read=false`



## Get A Specific Application

```ruby
require 'rest-client'

header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}
endpoint = 'https://api.hrpartner.io/application/'
applicationid = 8031

result = RestClient.get(endpoint + applicationid, header)
puts result

```

```shell
curl "https://api.hrpartner.io/application/8031"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"

```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};
var endpoint = "https://api.hrpartner.io/application/";
var applicationid = 8031;

client.get(endpoint + applicationid, info, function(data, response) {
  console.log(response;
});

```

> The above command returns JSON structured like this:

```json
{
  "id": 8031,
  "applicant": {
    "id": "yy8WXZNs1QLr8vpSNBICqA",
    "first_names": "Bernice",
    "last_name": "Flanders",
    "full_name": "Flanders, Bernice",
    "email": "bernice@mailinator.com"
  },
  "stage": {
    "name": "First Interview"
  },
  "job_listing": {
    "id": "senior-javascript-developer-k0jd",
    "title": "Senior Javascript Developer",
    "publish_at": "2020-03-23",
    "unpublish_at": "2020-04-15",
    "department": "Operations",
    "location": "Sydney Branch",
    "position": "Programmer",
    "employment_status": "Full Time",
    "city": "Sydney",
    "state": "NSW",
    "country": "Australia",
    "postcode": "2510",
    "is_active": true
  },
  "custom_form": {
    "answers": {
      "areas-of-expertise": [
        "javascript",
        "html",
        "ruby"
      ],
      "experience-years": "15",
      "level-of-study": "other",
      "public-projects": "https://github.com/bernice_dev",
      "os-contributions": "no",
      "date-finished-study": "2002-10-31",
      "start-option": "1-month"
    }
  },
  "scorecards": [
    {
      "type": "user",
      "by": "Tricia McMillian",
      "item": "Appearance",
      "score": 4.0,
      "comment": "Neat and tidy - nice to see."
    },
    {
      "type": "user",
      "by": "Tricia McMillian",
      "item": "Communication",
      "score": 2.5,
      "comment": "Clear speaker. Strong accent though"
    },
    {
      "type": "user",
      "by": "Tricia McMillian",
      "item": "Attitude",
      "score": 4.0,
      "comment": ""
    },
    {
      "type": "user",
      "by": "Tricia McMillian",
      "item": "Presentation Pitch",
      "score": 2.5,
      "comment": ""
    },
    {
      "type": "user",
      "by": "Tricia McMillian",
      "item": "Whiteboard Test",
      "score": 3.0,
      "comment": "Haven't done this yet - waiting for next interview"
    },
    {
      "type": "user",
      "by": "Tricia McMillian",
      "item": "Technical Review",
      "score": 3.0,
      "comment": "Pinged Carol to do this later"
    }
  ],
  "attachments": [
    {
      "description": "Resume.pdf",
      "url": "_5jGmaQIuOL3uqyP6MU22Q/recruitment/3yM/Resume.pdf",
      "size": 74921
    },
    {
      "description": "references.pdf",
      "url": "_5jGmaQIuOL3uqyP6MU22Q/recruitment/3yM/references.pdf",
      "size": 274975
    }
  ],
  "interviews": [
    {
      "details": "First interview to talk to Bernice.",
      "venue": "Room B",
      "interview_at": "2020-03-22T02:00:00+00:00",
      "interview_end": null
    },
    {
      "details": "Hands on testing",
      "venue": "Lab A",
      "interview_at": "2020-03-26T00:00:00+00:00",
      "interview_end": "2020-03-26T04:30:00+00:00"
    }
  ],
  "comments": [
    {
      "type": "user",
      "by": "Tricia McMillian",
      "comment": "What does everyone think of her application? I thought doing it via the web was quite good, myself.",
      "updated_at": "2020-03-28T11:51:51+00:00"
    },
    {
      "type": "user",
      "by": "Trevor Carson",
      "comment": "It was a fairly simple web page, but good on her for doing it a little different!",
      "updated_at": "2020-03-29T11:52:32+00:00"
    }
  ],
  "is_closed": false,
  "is_active": true,
  "is_flagged": false,
  "is_archived": false,
  "is_hired": false,
  "is_read": true,
  "submitted_at": "2020-03-13T23:58:06+00:00",
  "source": "Indeed Apply 0123456789 [Targeted] [Sponsored]",
  "total_score": 3.0
}
```

This endpoint retrieves a single job application from the system using the **_Application ID_**.

### HTTP Request

`GET https://api.hrpartner.io/application/{applicationID}`

This call will return a single application based on the unique _Application ID_ from HR Partner.

<aside class="notice">Tip: You can use the <code>GET /applications</code> call to get a list of all application, then extract the <em>ID</em> field from the results to fetch individual applications.</aside>


## Add or Update An Application

```ruby
require 'rest-client'

# Update applicant details and application
postbody = {
  "applicant": {
    "first_names": "Patricia",
    "last_name": "Williams",
    "email": "patwilliams@mailinator.com"
  },
  "stage": {
    "name": "Second Interview"
  },
  "job_listing": {
    "id": "senior-javascript-developer-kj"
  },
  "custom_form": {
    "answers": {
      "areas-of-expertise": [
        "javascript",
				"html"
      ],
      "experience-years": "7",
      "level-of-study": "degree",
      "public-projects": "https://github.com/treehouse",
      "os-contributions": "no",
      "date-finished-study": "2015-12-31",
      "start-option": "1-month"
    }
  }
}

header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d', :body => postbody}
endpoint = 'https://api.hrpartner.io/application/'

result = RestClient.post(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/application"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
  -H "Content-Type: application/json"
  -X POST
  -d '{"applicant": {"first_names":"Patricia","last_name":"Williams","email":"patwilliams@mailinator.com"},"stage":{"name":"Second Interview"},"job_listing":{"id":"senior-javascript-developer-kj"},"custom_form":{"answers":{"areas-of-expertise":["javascript","html"],"experience-years":"7","level-of-study":"degree","public-projects":"https://github.com/treehouse","os-contributions":"no","date-finished-study":"2015-12-31","start-option":"1-month"}}}'
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();

// Update Arthur's record with tax number, update custom fields with new salary and work times, add contractor tag, change mobile number and add new email
var postbody = postbody = {
  "applicant": {
    "first_names": "Patricia",
    "last_name": "Williams",
    "email": "patwilliams@mailinator.com"
  },
  "stage": {
    "name": "Second Interview"
  },
  "job_listing": {
    "id": "senior-javascript-developer-kj"
  },
  "custom_form": {
    "answers": {
      "areas-of-expertise": [
        "javascript",
				"html"
      ],
      "experience-years": "7",
      "level-of-study": "degree",
      "public-projects": "https://github.com/treehouse",
      "os-contributions": "no",
      "date-finished-study": "2015-12-31",
      "start-option": "1-month"
    }
  }
}

var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}, body: postbody};
var endpoint = "https://api.hrpartner.io/application/";

client.post(endpoint, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this:

```json
{
  "id": 113,
  "applicant": {
    "id": "Us6iBUp30rl9fegVMBOlqA",
    "first_names": "Patricia",
    "last_name": "Williams",
    "full_name": "Williams, Patricia",
    "email": "patwilliams@mailinator.com"
  },
  "stage": {
    "name": "Second Interview"
  },
  "job_listing": {
    "id": "senior-javascript-developer-kj",
    "title": "Senior Javascript Developer",
    "publish_at": "2020-04-13",
    "unpublish_at": "2020-04-30",
    "department": "Production",
    "location": "Sydney Branch",
    "position": "Programmer",
    "employment_status": "Full Time",
    "city": "Sydney",
    "state": "NSW",
    "country": "Australia",
    "postcode": "2000",
    "is_active": true
  },
  "custom_form": {
    "answers": {
      "areas-of-expertise": [
        "javascript",
        "html"
      ],
      "experience-years": "7",
      "level-of-study": "degree",
      "public-projects": "https://github.com/treehouse",
      "os-contributions": "no",
      "date-finished-study": "2015-12-31",
      "start-option": "1-month"
    }
  },
  "scorecards": [],
  "attachments": [],
  "interviews": [],
  "comments": [],
  "is_closed": false,
  "is_active": true,
  "is_flagged": false,
  "is_archived": false,
  "is_hired": false,
  "is_read": true,
  "submitted_at": "2020-04-16T09:33:56+00:00",
  "source": "Entered via API [application]",
  "total_score": 0.0
}
```


This endpoint will either add a new application, or else update _certain fields_ for an existing application.

### HTTP Request

`POST https://api.hrpartner.io/application`

A successful POST will return a application object (see the `GET /application` call above) upon successful modification.

<aside class="warning">
  <strong>Note:</strong> This call will create the application if you do not specify the `id` field in the JSON POST body.  If you specify a valid ID then the application will be updated.  This call will also create the applicant if the email address does not already exist in the system, or it will update the details of the applicant if the email address already exists.
</aside>

### POST Body

The JSON packet that can be POSTed to the endpoint is a subset of the JSON that you receive from the GET call to the `/application` endpoint.

Parameter | Type | Description
--------- | ---- | -----------
id | numeric | (Optional) - Specify an existing id to update it.  Leave this field off if you want to create a new application


The following describes the fields in the `applicant` tree:

Parameter | Type | Description
--------- | ---- | -----------
email<sup>*</sup> | text | The applicant email address
first_names | text | The applicants first name
last_name | text| The applicants last name


The following describes the fields in the `job_listing` tree:

Parameter | Type | Description
--------- | ---- | -----------
id<sup>*</sup> | text | The job listing unique slug (see `/job_listing` endpoint)


The following described the fields in the `stage` tree:

Parameter | Type | Description
--------- | ---- | -----------
name | text | The stage of the job application pipeline that the candidate is in (must be an existing stage name)


_<sup>*</sup> - Mandatory (required) field_


<aside class="info">
  <strong>Note:</strong> You can change the Stage of the pipeline that the applicant is in by specifying an existing applicant email and name in the `applicant` section of the POST body, then specifying the job listing ID in the `job_listing` section and the Stage name in the `stage` section.  Specifying a different Stage name will just move the applicant into that stage immediately.

  If you specify an invalid Stage name, then the company default stage (usually 'Applied') will be allocated to the application.
</aside>


#### Custom Form Fields

You can also specify the custom form fields for the application in the POST body.  There is a section called `custom_form` and a subsection called `answers`.  You will need to specify the field names that you have defined in your custom form, and the answers to them in here.

<aside class="warning">
  We do not do any cross checking for valid custom form field names.  If you specify an invalid field name or contents, then it will simply be ignored by our form renderer when you are viewing the application later.  We strongly recomment that you call <strong>GET /job_listing</strong> to get the specific job listing first which will show you the custom form field names associated with the job listing, then use this information to build the answer object.
</aside>

For example, assuming you make a call to the `job_listing` endpoint, and within the returned data, you see it will look as per our sample _(EX.1)_ on the right.


> _(EX.1)_ A sample of part of the JSON object returned by the `GET job_listing` API call which contains the custom form question data:

```json
...
"custom_form": {
    "name": "Developer Questions",
    "fields": [
      {
        "type": "checkbox-group",
        "label": "Areas of expertise",
        "name": "areas-of-expertise",
        "values": [
          {
            "label": "Javascript",
            "value": "javascript"
          },
          {
            "label": "HTML",
            "value": "html"
          },
          {
            "label": "Ruby",
            "value": "ruby"
          },
          {
            "label": "PHP",
            "value": "php"
          }
        ]
      },
      {
        "type": "number",
        "label": "Years of programming experience",
        "className": "form-control",
        "name": "experience-years",
        "min": "0",
        "max": "99",
        "step": "1"
      },
      {
        "type": "select",
        "label": "Have you completed a tertiary level of study in programming?",
        "className": "form-control",
        "name": "level-of-study",
        "values": [
          {
            "label": "No",
            "value": "no",
            "selected": true
          },
          {
            "label": "High school level only",
            "value": "high-school"
          },
          {
            "label": "Certificate or Associate Diploma",
            "value": "certificate-diploma"
          },
          {
            "label": "Computer Science Degree",
            "value": "degree"
          },
          {
            "label": "Internship/Other",
            "value": "other"
          }
        ]
      },
      {
        "type": "text",
        "label": "Public Projects",
        "placeholder": "Links to your Github page  blog  web site or other evidence of your programming skills",
        "className": "form-control",
        "name": "public-projects",
        "subtype": "text"
      },
      {
        "type": "radio-group",
        "required": true,
        "label": "Do you contribute to open source software?",
        "inline": true,
        "name": "os-contributions",
        "values": [
          {
            "label": "Yes",
            "value": "yes",
            "selected": true
          },
          {
            "label": "No",
            "value": "no"
          }
        ]
      },
      {
        "type": "date",
        "label": "Year Finished Study",
        "className": "form-control",
        "name": "date-finished-study"
      },
      {
        "type": "radio-group",
        "label": "When Can You Start?",
        "name": "start-option",
        "values": [
          {
            "label": "Immediately",
            "value": "immediately",
            "selected": true
          },
          {
            "label": "Within1 Month",
            "value": "1-month"
          },
          {
            "label": "Within 3 Months",
            "value": "3-month"
          },
          {
            "label": "By End Of Year",
            "value": "year-end"
          }
        ]
      }
    ]
  },
 ...
```

You will need to look at the `fields` -> `name` definitions here, which will show you the field names of: _areas-of-expertise_, _experience-years_, _level-of-study_, _public-projects_, _os-contributions_, _date-finished-study_ and _start-option_.

So to build the `answer` object, you will need to structure it as shown like _(EX.2)_ on the right.

> _(EX.2)_ How you should structure the `answers` section in the POST body of the JSON data you send back to us:

```json
...
  "custom_form": {
    "answers": {
      "areas-of-expertise": ["javascript","html"],
      "experience-years": "7",
      "level-of-study": "degree",
      "public-projects": "https://github.com/treehouse",
      "os-contributions": "no",
      "date-finished-study": "2015-12-31",
      "start-option": "1-month"
    }
  },
...
```


## Get Application Stage Tracking

```ruby
require 'rest-client'

endpoint = 'https://api.hrpartner.io/application_stage_tracking/'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/application_stage_tracking"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/application_stage_tracking";
var info = {headers: {"x-api-key":"ee095c2f58da4f36d087ca7794384f4d"}};

client.get(endpoint, info, function(data, response) {
  console.log(response;
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 120458,
    "applicant_id": "u4GDSDaNxTED6hVzstyPMw",
    "applicant_email": "shaydefoye@mailinator.com",
    "applicant_name": "Foye, Shayde",
    "job_id": "warehouse-assistant-lk",
    "job_title": "Warehouse Assistant",
    "changed_at": "2020-06-12T02:14:50+00:00",
    "from_stage": "Interview",
    "to_stage": "Job Offer"
  },
  {
    "id": 120613,
    "applicant_id": "u4GDSDaNxTED6hVzstyPMw",
    "applicant_email": "shaydefoye@mailinator.com",
    "applicant_name": "Foye, Shayde",
    "job_id": "warehouse-assistant-lk",
    "job_title": "Warehouse Assistant",
    "changed_at": "2020-06-12T02:15:18+00:00",
    "from_stage": "Job Offer",
    "to_stage": "Rejected"
  },
  {
    "id": 120655,
    "applicant_id": "hnR8RHJZdSD6VrJUe0hEhw",
    "applicant_email": "nestakaisin@mailinator.com",
    "applicant_name": "Kaisin, Nesta",
    "job_id": "warehouse-assistant-lk",
    "job_title": "Warehouse Assistant",
    "changed_at": "2020-06-12T02:15:42+00:00",
    "from_stage": "Applied",
    "to_stage": "Interview"
  },
  {
    "id": 120780,
    "applicant_id": "XjnGAvV2he8fHfm-PqilQQ",
    "applicant_email": "raydeleter@mailinator.com",
    "applicant_name": "Deleter, Raymond",
    "job_id": "senior-javascript-developer-kj",
    "job_title": "Senior Javascript Developer",
    "changed_at": "2020-06-12T02:19:23+00:00",
    "from_stage": "Second Interview",
    "to_stage": "Job Offer"
  },
  {
    "id": 120818,
    "applicant_id": "xU6ilFbi5Ix6qYbfneipiw",
    "applicant_email": "ianturpington@mailinator.com",
    "applicant_name": "Turpington, Ian",
    "job_id": "warehouse-manager--distribution--zd",
    "job_title": "Warehouse Manager (Distribution)",
    "changed_at": "2020-06-12T02:21:26+00:00",
    "from_stage": "Applied",
    "to_stage": "Initial Contact"
  },
  {
    "id": 120943,
    "applicant_id": "xU6ilFbi5Ix6qYbfneipiw",
    "applicant_email": "ianturpington@mailinator.com",
    "applicant_name": "Turpington, Ian",
    "job_id": "warehouse-manager--distribution--zd",
    "job_title": "Warehouse Manager (Distribution)",
    "changed_at": "2020-06-12T02:24:44+00:00",
    "from_stage": "Initial Contact",
    "to_stage": "First Interview"
  },
  {
    "id": 121011,
    "applicant_id": "Z4tDh4U7tYbkTIF2-DkSrg",
    "applicant_email": "suzein@mailinator.com",
    "applicant_name": "Norton, Susan",
    "job_id": "warehouse-manager--distribution--zd",
    "job_title": "Warehouse Manager (Distribution)",
    "changed_at": "2020-06-12T02:24:56+00:00",
    "from_stage": "(none)",
    "to_stage": "First Interview"
  },
  {
    "id": 121098,
    "applicant_id": "xFqp67fLgzUMCEP_l8wC9Q",
    "applicant_email": "stevecreole@mailinator.com",
    "applicant_name": "Creole, Steve",
    "job_id": "warehouse-manager--distribution--zd",
    "job_title": "Warehouse Manager (Distribution)",
    "changed_at": "2020-06-12T02:25:14+00:00",
    "from_stage": "(none)",
    "to_stage": "First Interview"
  },
  {
    "id": 121151,
    "applicant_id": "xFqp67fLgzUMCEP_l8wC9Q",
    "applicant_email": "stevecreole@mailinator.com",
    "applicant_name": "Creole, Steve",
    "job_id": "warehouse-manager--distribution--zd",
    "job_title": "Warehouse Manager (Distribution)",
    "changed_at": "2020-06-12T02:36:17+00:00",
    "from_stage": "First Interview",
    "to_stage": "Second Interview"
  }
]
```

This endpoint retrieves all job applications stage tracking information in the system.

### HTTP Request

`GET https://api.hrpartner.io/application_stage_tracking`

This call will retrieve all job application tracking information in the system.  This helps you to build a trail of the movement of job applications within your recruitment module over time, and can also help you to trigger certain actions when applicants reach a particular stage in a job application..

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
job | text | Return only application tracking for this job ID.
applicant | text | Return only application tracking for this applicant email or unique ID.
from_stage | text | Return tracking data that moved FROM this stage name.
to_stage | text | Return tracking data that moved TO this stage name.
changed_at_from, changed_at_to | date (yyyy-mm-dd) | Fetch only application tracking that happened between these two dates.


### Examples

To get a list of all application tracking for from 1st to 30th June 2020:

`GET https://api.hrpartner.io/application_stage_tracking?changed_at_from=2020-06-01&changed_at_to=2020-06-30`

To get all application tracking for applicant steve@mycompany.com which moved to the 'Interview' stage:

`GET https://api.hrpartner.io/application_stage_tracking?applicant=steve@mycompany.com&to_stage=Interview`

To get all application tracking for the job `delivery-truck-driver-oh6P` where the applicants moved on from the 'Reference Check' stage:

`GET https://api.hrpartner.io/application_stage_tracking?job=delivery-truck-driver-oh6P&from_stage=Reference Check`







# Timesheets

(Timesheet information is still being written - please check back later)


# Modules

Some calls to the API require you to specify a _Module_ that the data belongs to.  Here are the current modules in HR Partner for your reference, and the string you can use to specify a particular module during a call:

Name | Refers To
---- | -----------
_employee_ | Employee masterfile
_reminder_ | Reminders module
_timesheet_ | Timesheet sequences
_singletimesheet_ | A particular timesheet
_expense_ | Expenses module
 | **_Employee Submodules_**
_absence_ | Leave/Time Off/Absences module
_asset_ | Company assets module
_attachment_ | File attachments in system
_benefit_ | Benefits & packages module
_dependent_ | Employee dependents module
_education_ | Prior Education module
_grievance_ | Grievances module
_interview_ | Interview/Meetings module
_note_ | General employee notes module
_position_ | Position & Salary module
_renewable_ | Renewable documents module
_review_ | Performance Review module
_skill_ | Skills matrix module
_training_ | Training module

