# Invoices

## Invoices Adding API

```shell
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/invoices"
  -H "Authorization: token_xxx"
```

```javascript
// Updating
```

> The above command returns success JSON structured like this:

```json
{
  "success": true,
  "data": [
      {
          "XtendisRefID": "6572495920",
          "InvoiceStatus": "OK"
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
        "InvoiceStatus": "Failed",
        "StatusDetails": "Please resend"
      },
    ],
  }
```

This endpoint to add an invoice.

### HTTP Request

`POST https://fc-api.test.financecenter.sfs360.io/api/v1/invoices`

### Headers
Key | Value | Description
--------- | ------- | -----------
Authorization | {{jwtToken}} | Token


### Body Parameters

Parameter | Type | Description | Required
--------- | ------- | ----------- | -
Admin | String | Administration | Yes
AmountExVAT | Number | Amount excl. VAT | Yes
AmountVAT | Number | Amount VAT | Yes
BlockCode | String | Block Code (Existing in SFS 360 system) | Yes
CreditorID | Number | Invoice Creditor ID (existing in SFS 360 system) | Yes
CreditorName | String | The SFS Creditor name | Yes
Currency | String | Currency Code( 3 Character) | Yes
DateOfEntry |  Date | Date Of Entry (Format YYYY-MM-DD) | Yes
Duplicate | String | Duplicate Y/N | Yes
EmailAddressSender | String | Email Address | Yes
ExternalInvoiceNumber | String | External Invoice Number | Yes
FlightDate | Date | Flight Date (Format YYYY-MM-DD) | No
FlightNumber | String | Flight Number | No
InvoiceDate | Date | Invoice Date (Format YYYY-MM-DD) | Yes
InvoiceID | Number | Invoice ID | Yes
InvoiceType | String | Invoice Type - Values: D or C | Yes
LinkInvoice | String | Tthe link to the extendis invoice pdf | Yes
SepaNumber | Number | The SEPA banknumber of the creditor | Yes
TotalAMountInclVAT | Number | Total Amount Inc. VAT | Yes
VatNumber | String | The VAT number of the creditor (existing in SFS 360 system) | Yes
XtendisRefID | String | Extendis Ref ID | Yes

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
