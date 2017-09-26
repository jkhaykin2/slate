# AccountLists

## GET /accountlists

```shell
curl "https://app.engagio.com/api/v1/accountLists"
  -H "Authorization: Bearer engagio_v334asfsdfo3241ERqwefe"
```

> The above command returns JSON structured like this:

```javascript
var request = require('request');

request({
  headers: {
    'Authorization': 'Bearer engagio_v334asfsdfo3241ERqwefe',
    'Content-Type': 'application/json'
  },
    uri: 'https://app.engagio.com/api/v1/accountLists',
    method: 'GET'
  }, function (err, res, body) {
    var pJSON = JSON.parse(body);
    console.log(pJSON)
})
```

```json
[
  {
    "id": 213,
    "name": "Accounts with Opps - Presentation/Demo Stage"
  }
]
```

### HTTP Request

`GET https://app.engagio.com/api/v1/accountLists`

The AccountLists endpoint returns a JSON blob that contains a list of account lists in Engagio.

### Responses
<aside class="success">
<b>200 OK</b>
</aside>

*A JSON blob with the name and id of each account list*

<aside class="alert">
<b>400 Bad Request</b>
</aside>

*Invalid request*

<aside class="warning">
<b>500 Internal Server Error</b>
</aside>

*Server error occurred*

### How to find an AccountList id outside of the API

While the new accountLists API may be the easiest way to access the list ID, the other way to get the list ID is through the Engagio web application UI -- if you select the account list from the box in the top left, then the account list ID shows up as a path component in the URL (see screenshot below).

<img src="../images/accountlists.png" alt="Accountlists" class="al-screenshot">
