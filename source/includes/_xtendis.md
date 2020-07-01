# Xtendis

## Creditor Validation API

```shell
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/xtendis/creditors/validate"
  -H "Authorization: token_xxx"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
{
    "status" : "success",
    "data": [
        {
            "CreditorID": 6572495920,
            "VatNumber": "NL22927920-B02",
            "SepaNumber": "DZ580002100001113000000570",
            "CreditorStatus": 0
        }
    ],
}
```

This endpoint validate Creditor information.

### HTTP Request

`POST https://fc-api.test.financecenter.sfs360.io/api/v1/xtendis/creditors/validate`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
CreditorID | Number | The SFS Creditor ID (existing in SFS 360 system)
CreditorName | String | The SFS Creditor name
VatNumber | String | The VAT number of the creditor (existing in SFS 360 system)
SepaNumber | Number | The SEPA banknumber of the creditor

<aside class="notice">
Notice
</aside>
- `CreditorID`
    - Should be started with one of numbers 7, 8, 9.
    - If remove first number, the rest has to greater than 0.
    - Maximum 10 characters

## Blockcode Validation API

```shell
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/xtendis/creditors/validate"
  -H "Authorization: token_xxx"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
{
    "status" : "success",
    "data": [
        {
            "CreditorID": 6572495920,
            "VatNumber": "NL22927920-B02",
            "SepaNumber": "DZ580002100001113000000570",
            "CreditorStatus": 0
        }
    ],
}
```

This endpoint validate Creditor information.

### HTTP Request

`POST https://fc-api.test.financecenter.sfs360.io/api/v1/xtendis/creditors/validate`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
CreditorID | Number | The SFS Creditor ID (existing in SFS 360 system)
CreditorName | String | The SFS Creditor name
VatNumber | String | The VAT number of the creditor (existing in SFS 360 system)
SepaNumber | Number | The SEPA banknumber of the creditor

<aside class="notice">
Notice
</aside>
- `CreditorID`
    - Should be started with one of numbers 7, 8, 9.
    - If remove first number, the rest has to greater than 0.
    - Maximum 10 characters
