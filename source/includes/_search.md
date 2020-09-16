## Search API

```shell
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/{__MODULE_NAME__}/search"
  -H "Authorization: token_xxx"
```
Notice: 

- `__MODULE_NAME__` : creditor Or debtors Or invoices/outgoing Or invoices/incoming Or invoices/expected

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
        "Name": "Creditor 1",
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

This endpoint Search a Document.

### HTTP Request

`POST https://fc-api.test.financecenter.sfs360.io/api/v1/{__MODULE_NAME__}/search`

Notice: 

- `__MODULE_NAME__` : creditor Or debtors Or invoices/outgoing Or invoices/incoming Or invoices/expected

### Query Parameters

Parameter | | Type | Description | Required
--------- | ------- | ------- | ----------- | -----------
PartitionKey | |  Array | Array PartitionKey Value (Hashkey) Value, Ex: [99000] (Required) | Yes
Filter | |  Array | Array filter condition | No
 - | Key | String | Field Name To Search
 - | Operator | Enum | Operator (Default: equal)
 - | Value | Any | Value Of Field Search
Index |  | String | Field name Index To Sort | No
Sort |  | Enum | desc or asc - Sort ascending or desending | No
LastKey |  | Any | An object that you can pass into .startAt(lastkey) to retrieve more documents. | No

<aside class="notice">
Notice
</aside>

- `Operator`: ['contains','greatThan','greatThanEqual','inArr','notInArr','lessThan','lessThanEqual']

- `Filter`
    - Example: 
  ```json
      "Filter": 
      [
        {
          "Key": "Name",
          "Operator": "contains",
          "Value": "test"
        }
     ]
  ```