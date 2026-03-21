# Employee Sub Modules

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
    "leave_type": "taken",
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
    "leave_type": "taken",
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
    "leave_type": "taken",
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

The Absences module contains the records for each employee's leave or vacation time taken off.  Now also includes any TOIL/Flexi time that has been added back as well.

### HTTP Request

`GET https://api.hrpartner.io/absences`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
employee | text | Specify the employee code to only see the absence records for that particular employee.
department | text | Specify one or more department names (separated by commas) to only show employee absences within that department.
location | text | Only return employees within this location.
group | text | Only return employees within this group.
type | text | Specifies whether you want "taken" leave records or "added" leave (TOIL/Flexi)
absence_reason | text | Return only absence records with this particular absence reason.
duration_from, duration_to | number | Return only leave records with a duration between these values (inclusive).
physician | text | Return record with this partial text in the physician name field.
certificate_number | text | Return records with this text within the certificate field.
absence_status | text | Return records which have this absence status set.
comments | text | Search for this text within the comments field and return those.
absence_date_from, absence_date_to | date (yyyy-mm-dd) | Return leave records that fall between these two dates (inclusive).
show_linked_request | true/false | Return extra information on any linked leave requests associated with this absence entry in a `linked_request` child object.

<aside class="warning">
  NOTE: When using the <code>show_linked_request=true</code> parameter, please be aware that it will slow down the returning of data considerably due to the many extra database calls the system will need to make.  Please ensure that you set other parameters on the main query to limit the number of records returned in order that the query does not time out.
</aside>aside>

### Examples

To get a list of all absence records for employee whose code is 'JONES':

`GET https://api.hrpartner.io/absences?employee=JONES`

To get all sick leave records approved by Dr. Smith:

`GET https://api.hrpartner.io/absences?physician=Smith&absence_reason=Sick Leave`

To get all 'Approved' leave records that occured during March 2020:

`GET https://api.hrpartner.io/absences?absence_date_from=2020-03-01&absence_date_to=2020-03-31&absence_status=Approved`

To get all TOIL/Flexi additions for the month of April 2020:

`GET https://api.hrpartner.io/absences?absence_date_from=2020-04-01&absence_date_to=2020-04-30&type=added`

To get all TOIL/Flexi entries for "London" location and include the associated employee requests information:

`GET https://api.hrpartner.io/absences?location=London&type=added&show_linked_request=true`


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
tags | text | Return only notes that have the matching hashtags.  Specify tags in a comma separated list without the leading '#' character.
include_events | true/false | Include event historical information on who added/changed/deleted the note. (Default: false)

### Examples

To get a list all notes for John Smith (employee code SMITJ):

`GET https://api.hrpartner.io/notes?employee=SMITJ`

To find all notes created in March 2020:

`GET https://api.hrpartner.io/notes?created_date_from=2020-03-01&created_date_to=2020-03-31`

To find all notes that contain the word 'promotion' and were modified in the first week of March 2020:

`GET https://api.hrpartner.io/notes?note=promotion&updated_date_from=2020-03-01&updated_date_to=2020-03-08`

To find all notes for employee code WILSJ that have the '#late' or '#workshop' hashtags:

`GET https://api.hrpartner.io/notes?employee=WILSJ&tags=late,workshop`

To find all notes that have the '#warning' hashtag and include historical events data on who made changes:

`GET https://api.hrpartner.io/notes?tags=warning&include_events=true`

### Attachments

If a note includes attachments, they will be returned as an object array underneath the main note record.  The structure of this object is:

Parameter | Type | Description
--------- | ---- | -----------
description | text | The file name
url | text | The URL path to the file
size | number | The size of the file in bytes

### Events

If you choose to include event details showing who made changes to the note, then the structure of this object is:

Parameter | Type | Description
--------- | ---- | -----------
action | text | The action type (either "Added", "Changed" or "Deleted")
actioned_at | datetime | The date and time that the action took place
actioned_by | text | The name of the admin user who created the action


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


