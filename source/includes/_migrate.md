# Migrate

```shell
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/migrate"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns success JSON structured like this:

```json
{
    "success": true,
    "data": []
  }
```

This endpoint migrate all table.

### HTTP Request

`POST https://fc-api.test.financecenter.sfs360.io/api/v1/migrate`

### Body Parameters

Parameter | Type | Description
--------- | ------- | -----------
version | String | Version (Example:"1.0")


<aside class="notice">
Notice
</aside>

- Delete table if already existing before migrate.
