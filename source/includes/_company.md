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
