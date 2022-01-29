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
    "custom_form": {
      "answers": {
        "why-work-for-us": "Because I am a great driver!",
        "biggest-achievements": "",
        "current-licence-number": "AAA12345",
        "years-held": "10",
        "vehicle-licences": [
          "truck-rigid",
          "truck-prime-mover"
        ],
        "licence-state": "OH",
        "last-currency-check": "",
        "licence-endorsements": [
          "class-a"
        ]
      }
    },
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
    "custom_form": {
      "answers": {
        "why-work-for-us": "Highly experienced and motivated.",
        "biggest-achievements": "Worked for the biggest trucking firm in the UK.",
        "current-licence-number": "H83374-A",
        "years-held": "32",
        "vehicle-licences": [
          "truck-rigid",
          "truck-prime-mover",
          "truck-articulated"
        ],
        "licence-state": "AL",
        "last-currency-check": "2019-04-15",
        "licence-endorsements": [
          "class-b",
          "class-c"
        ]
      }
    },
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
    "custom_form": {
      "answers": {
        "why-work-for-us": "Been out of work for 2 years now.",
        "biggest-achievements": "",
        "current-licence-number": "38847663",
        "years-held": "5",
        "vehicle-licences": [
          "car-sedan",
          "small-van"
        ],
        "licence-state": "NY",
        "last-currency-check": "2020-04-13",
        "licence-endorsements": [
          "class-a"
        ]
      }
    },
    "source": "Entered by Arthur Dent",
    "submitted_at": "2020-05-28T09:29:25+00:00",
    "is_flagged": false,
    "is_archived": false,
    "is_hired": false,
    "is_read": false
  }
]
```

This endpoint retrieves all job applications (and the answers to the custom form questions, if any) for a particular job listing that are currently in the system.

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
    "name": "Developer Screening Questions",
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
    "name": "Developer Screening Questions",
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

endpoint = 'https://api.hrpartner.io/stage/track/'
header = {'x-api-key' => 'ee095c2f58da4f36d087ca7794384f4d'}

result = RestClient.get(endpoint, header)

puts result
```

```shell
curl "https://api.hrpartner.io/stage/track"
  -H "x-api-key:ee095c2f58da4f36d087ca7794384f4d"
```

```javascript
var Client = require('node-rest-client').Client;
 
var client = new Client();
var endpoint = "https://api.hrpartner.io/stage/track";
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
    "applicant_first_names": "Shayde",
    "applicant_last_name": "Foye",
    "applicant_full_name": "Foye, Shayde",
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
    "applicant_first_names": "Shayde",
    "applicant_last_name": "Foye",
    "applicant_full_name": "Foye, Shayde",
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
    "applicant_first_names": "Nesta",
    "applicant_last_name": "Kaisin",
    "applicant_full_name": "Kaisin, Nesta",
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
    "applicant_first_names": "Raymond",
    "applicant_last_name": "Deleter",
    "applicant_full_name": "Deleter, Raymond",
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
    "applicant_first_names": "Ian",
    "applicant_last_name": "Turpington",
    "applicant_full_name": "Turpington, Ian",
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
    "applicant_first_names": "Ian",
    "applicant_last_name": "Turpington",
    "applicant_full_name": "Turpington, Ian",
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
    "applicant_first_names": "Susan",
    "applicant_last_name": "Norton",
    "applicant_full_name": "Norton, Susan",
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
    "applicant_first_names": "Steve",
    "applicant_last_name": "Creole",
    "applicant_full_name": "Creole, Steve",
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
    "applicant_first_names": "Steve",
    "applicant_last_name": "Creole",
    "applicant_full_name": "Creole, Steve",
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

`GET https://api.hrpartner.io/stage/track`

This call will retrieve all job application tracking information in the system.  This helps you to build a trail of the movement of job applications within your recruitment module over time, and can also help you to trigger certain actions when applicants reach a particular stage in a job application.

<aside class="info">
  <strong>NOTE:</strong> This API call is limited to 500 records in response to preserve our server resources, due to the large number of tracking transactions that can exist in a company that does a lot of hiring.  We highly recommend that you use one of the query parameters below to filter your requests to return less than 500 results.
</aside>


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

`GET https://api.hrpartner.io/stage/track?changed_at_from=2020-06-01&changed_at_to=2020-06-30`

To get all application tracking for applicant steve@mycompany.com which moved to the 'Interview' stage:

`GET https://api.hrpartner.io/stage/track?applicant=steve@mycompany.com&to_stage=Interview`

To get all application tracking for the job `delivery-truck-driver-oh6P` where the applicants moved on from the 'Reference Check' stage:

`GET https://api.hrpartner.io/stage/track?job=delivery-truck-driver-oh6P&from_stage=Reference Check`


