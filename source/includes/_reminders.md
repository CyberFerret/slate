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


