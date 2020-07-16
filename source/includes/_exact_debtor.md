# Exact > Debtor

## Debtor Create API

```shell
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/exact/debtors"
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
        "Debtor": 4000000111,
        "Name": "Exact Software Nederland B.V.",
        "SearchCode": "EXACT",
        "Country": "NL",
        "PostalCode": "2629 JD",
        "Address1": "Molengraaffsingel 33",
        "City": "Delf t",
        "Telephone": "+31 157115100",
        "Email": "info@exact.com",
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

This endpoint Create A Debtor.

### HTTP Request

`POST https://fc-api.test.financecenter.sfs360.io/api/v1/exact/debtors`

### Headers
Key | Value | Description
--------- | ------- | -----------
Authorization | {{jwtToken}} | Token


### Body Parameters

Parameter | Type | Description
--------- | ------- | -----------
Debtor | Number | The SFS Debtor ID (existing in SFS 360 system)
AdmNr | Number | Administration number 
Name | String | Name
SearchCode | String | Search Code
Country | String | Country (ISO land code)
PostalCode | String | Postal Code
Address1 | String | Address
City | String | City
Telephone | String | Telephone Number (Optional)
Email | String | Email Address (Optional)
BankInfo.BankAccType | String | Bank type - IBA or INT
BankInfo.BankAccNr | String | Bank account number 
BankInfo.BankCurrCode | String | Currency code 
BankInfo.BankTypePrimary | Number | Primary
BankInfo.BankName | String | Bank name 
BankInfo.BankSwiftAddress | String | Bic/Swift code 


<aside class="notice">
Notice
</aside>

- `Debtor`
    - Should be started with one of numbers 4, 5, 6.
    - If remove first number, the rest has to greater than 0.
    - Maximum 10 characters  
- `Bank Type`
    - IBA = International Bank Account number (With validation check)
    - INT = International number (Without validation check)
- `Primary`
    - Fixed value: 203201 

## Debtor Update API

```shell
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/exact/debtors/{DebtorID}"
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
        "Debtor": 4000000111,
        "Name": "Exact Software Nederland B.V.",
        "SearchCode": "EXACT",
        "Country": "NL",
        "PostalCode": "2629 JD",
        "Address1": "Molengraaffsingel 33",
        "City": "Delf t",
        "Telephone": "+31 157115100",
        "Email": "info@exact.com",
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

This endpoint Update Debtor information (Without Bank Account Information)

### HTTP Request

`PUT https://fc-api.test.financecenter.sfs360.io/api/v1/exact/debtors/{DebtorID}`

### Query Parameters
Parameter | Type | Description
--------- | ------- | -----------
DebtorID | Number | The SFS Debtor ID (existing in SFS 360 system)

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
Email | String | Email Address (Optional)

<aside class="notice">
Notice
</aside>

- `DebtorID`
    - Should be started with one of numbers 4, 5, 6.
    - If remove first number, the rest has to greater than 0.
    - Minimum 7 characters
    - Maximum 10 characters

## Debtor Update Bank Account API

```shell
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/exact/debtors/{DebtorID}/bank-accounts"
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
            "SearchCode": "EXACT",
            "Telephone": "+31 157115100",
            "PostalCode": "3029 SS",
            "Email": "info@exact.com",
            "Country": "NL",
            "Address1": "Molengraaffsingel 11",
            "City": "Delf t",
            "AdmNr": 99000,
            "Debtor": 4000000111,
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

This endpoint Update Debtor information.
### HTTP Request

`PATCH https://fc-api.test.financecenter.sfs360.io/api/v1/exact/debtors/{DebtorID}`

### Query Parameters
Parameter | Type | Description
--------- | ------- | -----------
DebtorID | Number | The SFS Debtor ID (existing in SFS 360 system)

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
Email | String | Email Address (Optional)
BankInfo.BankAccType | String | Bank type - IBA or INT 
BankInfo.BankAccNr | String | Bank account number 
BankInfo.BankCurrCode | String | Currency code 
BankInfo.BankTypePrimary | Number | Primary
BankInfo.BankName | String | Bank name 
BankInfo.BankSwiftAddress | String | Bic/Swift code 

<aside class="notice">
Notice
</aside>

- `DebtorID`
    - Should be started with one of numbers 4, 5, 6.
    - If remove first number, the rest has to greater than 0.
    - Minimum 7 characters
    - Maximum 10 characters  
- `Bank Type`
    - IBA = International Bank Account number (With validation check)
    - INT = International number (Without validation check)
- `Primary`
    - Fixed value: 203201 

## Debtor Find API

```shell
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/exact/debtors/{DebtorID}?AdminNr={AdmNr}"
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
        "Email": "testmail@gmail.com",
        "JournalNr": "0",
        "VatCode": "",
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

This endpoint Find A Debtor

### HTTP Request

`GET https://fc-api.test.financecenter.sfs360.io/api/v1/exact/debtors/{DebtorID}?AdminNr={AdmNr}`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
DebtorID | Number | The SFS Debtor ID (existing in SFS 360 system)
AdmNr | Number | Administration number  

<aside class="notice">
Notice
</aside>

- `DebtorID`
    - Should be started with one of numbers 4, 5, 6.
    - If remove first number, the rest has to greater than 0.
    - Minimum 7 characters
    - Maximum 10 characters 
