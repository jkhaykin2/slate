# Activities

## GET /activities/fields

```shell
curl "https://app.engagio.com/api/v1/activities/fields"
  -H "Authorization: Bearer engagio_v334asfsdfo3241ERqwefe"
```

> The above command returns JSON structured like this:

```json
[
  {
    "name": "{Activity}.category___e",
    "label": "Category",
    "dataType": "String",
    "pickListValues": [],
    "cardinality": -1,
    "status": "Normal",
    "referenceTo": []
  }
]
```

### HTTP Request

`GET https://app.engagio.com/api/v1/activities/fields`

The Activities Fields endpoint returns a list of all fields that are available to be returned via the /activities endpoint.

## GET /activities

```shell
curl "https://app.engagio.com/api/v1/activities?accountList=39&fields={Activity}.category___e&format=json"
  -H "Authorization: Bearer engagio_v334asfsdfo3241ERqwefe"
```

```javascript
var request = require('request');

request({
  headers: {
    'Authorization': 'Bearer engagio_v334asfsdfo3241ERqwefe',
    'Content-Type': 'application/json'
  },
    uri: 'https://app.engagio.com/api/v1/activities?accountList=39&fields={Activity}.category___e&format=json',
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
    "{Activity}.category___e": "Marketing Email Open",
    "{Activity}.id":3593215
  },
  {
    "{Activity}.category___e": "Marketing Email Open",
    "{Activity}.id":3769345
  }
]
```

The Activities endpoint returns a CSV file or JSON blob that contains details about people in an Engagio account list. Use the fields parameter to specify the desired fields to return.

❗ Either accountList or account parameter must be provided as well as at least one of the fields you want.

### HTTP Request

`GET https://app.engagio.com/api/v1/activities`

### Query Parameters

Parameter | Type | Description
--------- | ---- | -----------
fields | query integer | Names of fields to return. Call /activities/fields to learn available fields.
accountList | query integer  | ID of the Engagio account list whose activities should be returned.
account | query integer  | ID of the Engagio account to return data for.
filters | query object[], multiple parameters (filters=aaa&filters=bbb) | Filters to apply to limit the data returned.
format | query string (i.e. &format=json)  | Specify JSON to receive output as a JSON object as opposed to the .csv file output.
from | query string (ISO date) | The start date for the date range used for engagement-related fields, in ISO format.
to | query string (ISO date) | The end date for the date range used for engagement-related fields, in ISO format.

### Responses
<aside class="success">
<b>200 OK</b>
</aside>

*A CSV file with one row per activity and one column per requested field, unless "format=json" was specified*

<aside class="alert">
<b>400 Bad Request</b>
</aside>

*Invalid request*

<aside class="warning">
<b>500 Internal Server Error</b>
</aside>

*Server error occurred*
