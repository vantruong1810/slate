# Invoices

## Invoices Adding API

```shell
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/invoices"
  -H "Authorization: token_xxx"
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
    "data": [
      {
        "XtendisRefID": "6572495920",
        "InvoiceStatus": "OK",
      }
    ]
  }
```

> The above command returns fail JSON structured like this:

```json
{
    "success": false,
    "data": [
      {
        "XtendisRefID": "6572495920",
        "StatusDetails": "please resend",
      },
    ],
  }
```

This endpoint Add A Invoice.

### HTTP Request

`POST https://fc-api.test.financecenter.sfs360.io/api/v1/invoices`

### Headers
Key | Value | Description
--------- | ------- | -----------
Authorization | {{jwtToken}} | Token


### Body Parameters

Parameter | Type | Description
--------- | ------- | -----------
Creditor.CreditorID | Number | The SFS Creditor ID (existing in SFS 360 system)
Creditor.CreditorName | String | The SFS Creditor name
Creditor.VatNumber | String | The VAT number of the creditor (existing in SFS 360 system)
Creditor.SepaNumber | Number | The SEPA banknumber of the creditor
Invoice.Admin | String | Administration
Invoice.BlockCode | String | Block Code (Mandatory, Existing in SFS 360 system)
Invoice.ExternalInvoiceNumber | String | External Invoice Number
Invoice.CreditorID | Number | Invoice Creditor ID (existing in SFS 360 system)
Invoice.XtendisRefID | String | Extendis Ref ID
Invoice.InvoiceID | Number | Invoice ID
Invoice.InvoiceDate | Date | Invoice Date (Format YYYYMMDD)
Invoice.DateOfEntry |  Date | Date Of Entry (Format YYYYMMDD)
Invoice.Duplicate | String | Duplicate Y/N 
Invoice.AmountExVAT | Number | Amount excl. VAT 
Invoice.AmountVAT | Number | Amount VAT
Invoice.Currency | String | Currency Code( 3 Character)
Invoice.TotalAMountInclVAT | Number | Total Amount Inc. VAT
Invoice.EmailAddressSender | String | Email Address
Invoice.InvoiceType | String | Invoice Type - Values: D or C
Invoice.LinkInvoice | String | Tthe link to the extendis invoice pdf

<aside class="notice">
Notice
</aside>

- `CreditorID`
    - Should be started with one of numbers 7, 8, 9.
    - If remove first number, the rest has to greater than 0.
    - Minimum 7 characters
    - Maximum 10 characters

- `Duplicate`
    - Values: 0 or 1 ( 0=no 1=yes )

- `Currency`
    - Letter currency code ISO 4217

- `TotalAMountInclVAT`
    - = SUM AmountExVAT AND AmountVAT

- `InvoiceType`
    - D=Debit  C=Credit
