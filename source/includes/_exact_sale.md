# Exact > Sale Jounal

## Sale Create API

```shell
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/exact/sales"
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
    "success": true,
    "data": [
      {
        "AdmNr": 99000,
        "FinanceYear": 2020,
        "Period": 6,
        "JounalNr": 60,
        "EntryN": 202004000015,
        "Des": "Salesinvoice",
        "Date": "2020-06-07",
        "Debtor": 4000002,
        "Currency": "EUR",
        "Amount": "100",
        "ExchangeRate": 1,
        "DueDate": "2020-07-07",
        "DescLine": "Invoice line 1 with VAT",
        "AccountNumber": "4601",
        "VatCode": "0",
        "AmountExcludeVat": "100",
        "VatAmount": 0,
        "Quantity": 10,
        "PayMethod": 2,
      },
    ],
  }
```

This endpoint Create A Sale Jounal.

### HTTP Request

`POST https://fc-api.test.financecenter.sfs360.io/api/v1/exact/sales`

### Headers
Key | Value | Description
--------- | ------- | -----------
Authorization | {{jwtToken}} | Token


### Body Parameters

Parameter | Type | Description
--------- | ------- | -----------
AdmNr | Number | Administration number 
FinanceYear | Number | Format YYYY
Period | Number | Period
JounalNr | Number | Jounal Number
EntryNr | Number | Entry Number
Des | String | Description
Date | Date | Format YYYY-MM-DD
Debtor | Number | The SFS Creditor ID (existing in SFS 360 system)
Currency | String | Currency code 
Amount | Number | Amount
ExchangeRate | Number | Exchange Rate
DueDate | Date | Due Date
DescLine | String | DescLine 
AccountNumber | Number | Account Number
VatCode | String | Vat Code 
AmountExcludeVat | Number | Amount Exc.VAT
VatAmount | Number | VAT Amount
Quantity | Number | Quantity
PayMethod | Number | Bank = 2, Incasso = 4,

<aside class="notice">
Notice
</aside>

- `EntryNr`
    - Should be started with one of numbers 1, 2, 3.
    - If remove first number, the rest has to greater than 0.
    - Minimum 7 characters
    - Maximum 12 characters  

- `Debtor`
    - Should be started with one of numbers 4, 5, 6.
    - If remove first number, the rest has to greater than 0.
    - Minimum 7 characters
    - Maximum 10 characters
