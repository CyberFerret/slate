---
title: HR Partner API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - javascript

toc_footers:

  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - company
  - employees
  - employee_sub_modules
  - birthdays_anniversaries
  - lookups
  - reminders
  - recruitment
  - timesheets
  - expenses
  - projects
  - leave_requests
  - leave_balances
  - performances
  - modules
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

# Rate Limits

Our API currently has a rate limit of:

* 60 GET or POST requests per second
* A burst limit of 900 requests per 1 minute block  

Please consider this when making calls to our API, and please allow for some results to take up to 5 seconds to be returned.  We currently don't implement 'paging' on our result sets (yet), so it can take some time for a large packet of JSON data to be returned to you.

We have a general timeout of 60 seconds on API responses.  If you are constantly getting a 504 Timeout message, try adding some filter parameters to reduce the amount of data being returned to you.

# Disclaimer

Note: The API is still in 'early release' at this point in time, so the information below is subject to change with little notice.  Where possible, we will try not to make changes to our API interface which will break anything that was written using the older spec, but we reserve the right to make changes to improve performance or improve security without advanced notification during the early release phase.


---

