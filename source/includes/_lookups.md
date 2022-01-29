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
scorecards | Application scorecards
skill_names | Skill names
skill_ratings | Skill ratings
stages | Application stages
tags | Tags used within HR Partner
termination_reasons | List of termination reasons
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

