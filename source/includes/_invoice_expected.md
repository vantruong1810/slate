# Invoices Expected

## Calculate Total Amount API

```shell
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/invoices/expected/total-amount"
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
          "TotalAmountOpen": 230.00,
          "TotalAmountArchived": 250.00
      }
  ]
}
```

This endpoint to calculate total amount for Expected Invoice.

### HTTP Request

`POST https://fc-api.test.financecenter.sfs360.io/api/v1/invoices/expected/total-amount`

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
