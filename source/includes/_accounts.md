# Accounts

## GET /accounts/fields

```shell
curl "https://app.engagio.com/api/v1/accounts/fields"
  -H "Authorization: Bearer engagio_v334asfsdfo3241ERqwefe"
```

> The above command returns JSON structured like this:

```json
[
  {
    "name": "{Account}.engagementMinutesLast7Day",
    "label": "# Play Steps Resolved (all time)",
    "dataType": "Long",
    "pickListValues": [],
    "cardinality": -1,
    "status": "Normal",
    "referenceTo": []
  }
]
```

### HTTP Request

`GET https://app.engagio.com/api/v1/accounts/fields`

The Account Fields endpoint returns a list of all fields that are available to be returned via the /accounts endpoint.


## GET /accounts

```shell
curl "https://app.engagio.com/api/v1/accounts?accountList=39&fields={Account}.engagementMinutesLast7Day&format=json"
  -H "Authorization: Bearer engagio_v334asfsdfo3241ERqwefe"
```

```javascript
var request = require('request');

request({
  headers: {
    'Authorization': 'Bearer engagio_v334asfsdfo3241ERqwefe',
    'Content-Type': 'application/json'
  },
    uri: 'https://app.engagio.com/api/v1/accounts?accountList=39&fields={Account}.engagementMinutesLast7Day&format=json',
    method: 'GET'
  }, function (err, res, body) {
    var pJSON = JSON.parse(body);
    console.log(pJSON)
})
```

> The above command returns JSON structured like this:

```json
[
  {
    "{Account}.engagementMinutesLast7Days": 216.54,
    "{Account}.id": 6
  },
  {
    "{Account}.engagementMinutesLast7Days": 122.24199999999998,
    "{Account}.id": 8
  }
]
```

The Accounts endpoint returns a CSV file or JSON blob that contains details about accounts in an Engagio account list. Use the fields parameter to specify the desired fields to return.

❗ Either accountList or account parameter must be provided as well as at least one of the fields you want.

### HTTP Request

`GET https://app.engagio.com/api/v1/accounts`

### Query Parameters

Parameter | Type | Description
--------- | ---- | -----------
fields | query string[], multiple parameters (fields=aaa&fields=bbb) | Names of fields to return. Call /accounts/fields to learn available fields.
accountList | query integer | Description: ID of the Engagio account list whose accounts should be returned.
filters | query object[], multiple parameters (filters=aaa&filters=bbb) | Description: Filters to apply to limit the data returned.
format | query string (i.e. &format=json) | Description: Specify JSON to receive output as a JSON object as opposed to the .csv file output.
from | Type of Param:  query string (ISO date) | Description: The start date for the date range used for engagement-related fields, in ISO format.
to | Type of Param:  query string (ISO date) | Description: The end date for the date range used for engagement-related fields, in ISO format.

### Responses
<aside class="success">
<b>200 OK</b>
</aside>

*A CSV file with one row per account and one column per requested field, unless "format=json" was specified*

<aside class="alert">
<b>400 Bad Request</b>
</aside>

*Invalid request*

<aside class="warning">
<b>500 Internal Server Error</b>
</aside>

*Server error occurred*
