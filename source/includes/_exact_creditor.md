# Exact > Creditor

## Creditor Create API

```shell
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/creditors"
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
        "Creditor": 7000000001,
        "Name": "Exact Software Nederland B.V.",
        "SearchCode": "EXACT",
        "Country": "NL",
        "PostalCode": "2629 JD",
        "Address1": "Molengraaffsingel 33",
        "City": "Delf t",
        "Telephone": "+31 157115100",
        "Category": "HANDEL",
        "ContactEmail": "info@exact.com",
        "BankInfo": {
          "BankAccType": "IBA",
          "BankAccNr": "NL20RABO9038954298",
          "BankCurrCode": "EUR",
          "BankTypePrimary": 203201,
          "BankName": "Rabo bank",
          "BankSwiftAddress": "RABONL2U",
        },
      },
    ],
}
```

This endpoint Create A Creditor.

### HTTP Request

`POST https://fc-api.test.financecenter.sfs360.io/api/v1/creditors`

### Headers
Key | Value | Description
--------- | ------- | -----------
Authorization | {{jwtToken}} | Token


### Body Parameters

Parameter | Type | Description
--------- | ------- | -----------
Creditor | Number | The SFS Creditor ID (existing in SFS 360 system)
AdmNr | Number | Administration number 
Name | String | Name
SearchCode | String | Search Code
Country | String | Country (ISO land code)
PostalCode | String | Postal Code
Address1 | String | Address
City | String | City
Telephone | String | Telephone Number (Optional)
Category | String | Creditor category
ContactEmail | String | Email Address (Optional)
BankInfo.BankAccType | String | Bank type - IBA or INT
BankInfo.BankAccNr | String | Bank account number 
BankInfo.BankCurrCode | String | Currency code 
BankInfo.BankTypePrimary | Number | Primary
BankInfo.BankName | String | Bank name 
BankInfo.BankSwiftAddress | String | Bic/Swift code 


<aside class="notice">
Notice
</aside>

- `Creditor`
    - Should be started with one of numbers 7, 8, 9.
    - If remove first number, the rest has to greater than 0.
    - Minimum 7 characters
    - Maximum 10 characters  
- `Category`
    - PASSAG = passengers
    - HANDEL = all other creditors
- `Bank Type`
    - IBA = International Bank Account number (With validation check)
    - INT = International number (Without validation check)
- `Primary`
    - Fixed value: 203201 

## Creditor Update API (Put)

```shell
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/creditors/{creditorID}"
  -H "Authorization: token_xxx"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured success like this:

```json
{
    "success": true,
    "data": [
      {
        "AdmNr": 99000,
        "Creditor": 7000000001,
        "Name": "Exact Software Nederland B.V.",
        "SearchCode": "EXACT",
        "Country": "NL",
        "PostalCode": "2629 JD",
        "Address1": "Molengraaffsingel 33",
        "City": "Delf t",
        "Telephone": "+31 157115100",
        "Category": "HANDEL",
        "ContactEmail": "info@exact.com",
        "BankInfo": {
          "BankAccType": "IBA",
          "BankAccNr": "NL20RABO9038954298",
          "BankCurrCode": "EUR",
          "BankTypePrimary": 203201,
          "BankName": "Rabo bank",
          "BankSwiftAddress": "RABONL2U",
        },
      },
    ],
}
```

This endpoint Update Creditor information (Without Bank Account Information)

### HTTP Request

`PUT https://fc-api.test.financecenter.sfs360.io/api/v1/creditors/{CreditorID}`

### Query Parameters
Parameter | Type | Description
--------- | ------- | -----------
CreditorID | Number | The SFS Creditor ID (existing in SFS 360 system)

### Body Parameters

Parameter | Type | Description
--------- | ------- | -----------
AdmNr | Number | Administration number 
Name | String | Name
SearchCode | String | Search Code
Country | String | Country (ISO land code)
PostalCode | String | Postal Code
Address1 | String | Address
City | String | City
Telephone | String | Telephone Number (Optional)
Category | String | Creditor category
ContactEmail | String | Email Address (Optional)
BankInfo | Object | List Bank Account (Optional)
BankInfo.BankAccType | String | Bank type - IBA or INT 
BankInfo.BankAccNr | String | Bank account number 
BankInfo.BankCurrCode | String | Currency code 
BankInfo.BankTypePrimary | Number | Primary
BankInfo.BankName | String | Bank name 
BankInfo.BankSwiftAddress | String | Bic/Swift code

<aside class="notice">
Notice
</aside>

- `CreditorID`
    - Should be started with one of numbers 7, 8, 9.
    - If remove first number, the rest has to greater than 0.
    - Minimum 7 characters
    - Maximum 10 characters
- `Category`
    - PASSAG = passengers
    - HANDEL = all other creditors

## Creditor Update Information (Patch)

```shell
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/creditors/{CreditorID}"
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
            "Category": "HANDEL",
            "SearchCode": "EXACT",
            "Telephone": "+31 157115100",
            "PostalCode": "3029 SS",
            "ContactEmail": "info@exact.com",
            "Country": "NL",
            "Address1": "Molengraaffsingel 11",
            "City": "Delf t",
            "AdmNr": 99000,
            "Creditor": 7000000111,
            "BankInfo": [
                {
                    "BankAccType": "IBA",
                    "BankName": "Rabo bank",
                    "BankTypePrimary": 203201,
                    "BankAccNr": "NL09ABNA5766671156",
                    "BankCurrCode": "EUR",
                    "BankSwiftAddress": "RABONL2U"
                },
                {
                    "BankAccType": "IBA",
                    "BankName": "Rabo bank",
                    "BankTypePrimary": 203201,
                    "BankAccNr": "NL88ABNA9589603858",
                    "BankCurrCode": "EUR",
                    "BankSwiftAddress": "RABONL2U"
                }
            ],
            "Name": "Exact Softwaree test 3"
        }
    ]
}
```

This endpoint Update Creditor information.

### HTTP Request

`PATCH https://fc-api.test.financecenter.sfs360.io/api/v1/creditors/{CreditorID}`

### Query Parameters
Parameter | Type | Description
--------- | ------- | -----------
CreditorID | Number | The SFS Creditor ID (existing in SFS 360 system)

### Body Parameters

Parameter | Type | Description
--------- | ------- | -----------
AdmNr | Number | Administration number 
Name | String | Name (Optional)
SearchCode | String | Search Code (Optional)
Country | String | Country (ISO land code) (Optional)
PostalCode | String | Postal Code (Optional)
Address1 | String | Address (Optional)
City | String | City (Optional)
Telephone | String | Telephone Number (Optional)
Category | String | Creditor category (Optional)
ContactEmail | String | Email Address (Optional)
BankInfo | Object | List Bank Account (Optional)
BankInfo.BankAccType | String | Bank type - IBA or INT 
BankInfo.BankAccNr | String | Bank account number 
BankInfo.BankCurrCode | String | Currency code 
BankInfo.BankTypePrimary | Number | Primary
BankInfo.BankName | String | Bank name 
BankInfo.BankSwiftAddress | String | Bic/Swift code 

<aside class="notice">
Notice
</aside>

- `CreditorID`
    - Should be started with one of numbers 7, 8, 9.
    - If remove first number, the rest has to greater than 0.
    - Minimum 7 characters
    - Maximum 10 characters  
- `Bank Type`
    - IBA = International Bank Account number (With validation check)
    - INT = International number (Without validation check)
- `Primary`
    - Fixed value: 203201 

- `BankInfo`
    - If the request has BankInfo, the BankAccNr, BankAccNr, BankCurrCode, BankTypePrimary, BankName, BankSwiftAddress must be required.

- `AdmNr` must be required if the request has any params in the body parameters.

## Creditor Find API

```shell
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/exact/creditors/{creditorID}?AdminNr={AdmNr}"
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
        "Name": "test1",
        "SearchCode": "PAX1",
        "Country": "NL",
        "PostalCode": "2629 JD",
        "City": "HO CHI MINH",
        "Address": "ho chi minh",
        "Telephone": "+0084938979056",
        "ContactEmail": "testmail@gmail.com",
        "JournalNr": "0",
        "VatCode": "",
        "Category": "HANDEL",
        "BankAccountNr": [
            "NL05 ABNA 8014 5589 28",
            "NL12 RABO 5515 4397 24",
            "NL38 ABNA 4824 5388 31",
            "NL48 INGB 3470 4166 56",
            "NL73 RABO 5982 4824 71",
            "NL88 ABNA 9589 6038 58",
            "NL88 RABO 8871 0076 62"
        ]
        }
    ],
}
```

This endpoint Find A Creditor.

### HTTP Request

`GET https://fc-api.test.financecenter.sfs360.io/api/v1/exact/creditors/{CreditorID}?AdminNr={AdmNr}`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
CreditorID | Number | The SFS Creditor ID (existing in SFS 360 system)
AdmNr | Number | Administration number  

<aside class="notice">
Notice
</aside>

- `CreditorID`
    - Should be started with one of numbers 7, 8, 9.
    - If remove first number, the rest has to greater than 0.
    - Minimum 7 characters
    - Maximum 10 characters 
