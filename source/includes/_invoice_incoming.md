# Invoices Incoming

## Calculate Total Amount API

```shell
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/invoices/incoming/total-amount"
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
          "TotalPaid": 230.00,
          "TotalUnpaid": 250.00,
          "TotalDisputed": 250.00
      }
  ]
}
```

This endpoint to calculate total amount for Incoming Invoice.

### HTTP Request

`POST https://fc-api.test.financecenter.sfs360.io/api/v1/invoices/incoming/total-amount`

### Headers
Key | Value | Description
--------- | ------- | -----------
Authorization | {{jwtToken}} | Token


### Body Parameters

Parameter |  | Type | Description | Required
--------- | --------- | ------- | ----------- | -
DateFrom |  | Date | Date From (filter) | Yes
DateTo |  | Date | Date To (filter) | Yes
Filter | |  Array | Array filter condition | No
 - | Key | String | Field Name To Search
 - | Operator | Enum | Operator (Default: equal)
 - | Value | Any | Value Of Field Search

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

## Update Note Communication And Status Incoming Invoice API

```shell
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/invoices/{InvoiceNr}/incoming"
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
        "FinanceYear": 2020,
        "Creditor": 7000000111,
        "CreditorName": "Creditor 1",
        "InvoiceDate": 1598745600000,
        "InvoiceNr": 20800000008,
        "InvoiceType": "C",
        "Amount": 22.00,
        "Status": 1,
        "CreateAt": 1598745600000,
        "DateOfPayment": 1598745600000,
        "RealInvoiceNr": "LH000003",
        "BlockCode": "20200114_LG_H1_8888",
        "LinkInvoice": "https://extendis.com/invoice/684194461",
        "NoteCommunication": [
          {
            "NoteDate":"2020-28-27",
            "Content":"Test note form send communication" 
          }
        ],

        "CustomField": {
          "AirportName": "Brusel Airport",
          "FlightNumber": "LH2021",
          "FlightDate": 1598572800000,
          "InvoiceNrSFS": "LH23423536",
        },
      }
  ]
}
```

This endpoint to calculate total amount for Incoming Invoice.

### HTTP Request

`PUT https://fc-api.test.financecenter.sfs360.io/api/v1/invoices/{InvoiceNr}/incoming`

### Headers
Key | Value | Description
--------- | ------- | -----------
Authorization | {{jwtToken}} | Token


### Body Parameters

Parameter | Type | Description | Required
--------- | ------- | ----------- | -
NoteCommunication | Any | Note For Comunication  | No
Type | String | Date To (filter) | No
FinanceYear | Number | PartitionKey Value to Update | Yes
Status | Number | Status Value Update | No

<aside class="notice">
Notice
</aside>

- `NoteCommunication`:  with example format:
```json
  [
    {
      "NoteDate": "2020-28-27",
      "Content": "test note"
    }
  ]
```
- `Status`: 1 : Paid - 2: Unpaid - 3: Disputed
