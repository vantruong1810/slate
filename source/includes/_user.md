# User

## User Registration API

```shell
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/users/register"
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
        "Birthday": "2020-01-07",
        "Country": "NL",
        "DisplayName": "UserTest1",
        "Email": "test@gmail.com",
        "ID": "52907745-7672-470e-a803-a2f8feb52944",
        "Name": {
          "FirstName": "Test",
          "LastName": "user 2"
        },
        "PhoneNumber": "+31 89076414678",
        "Role": "User",
        "Status": "Active",
      },
    ],
  }
```

This endpoint Register A User.

### HTTP Request

`POST https://fc-api.test.financecenter.sfs360.io/api/v1/users/register`

### Headers
Key | Value | Description
--------- | ------- | -----------
Content-Type | application/json | Content Type


### Body Parameters

Parameter | Type | Description
--------- | ------- | -----------
ConfirmPassword | String | Confirm Password
Country | String | Country (ISO land code)
DisplayName | String | Display Name
Email | String | Email Register
FirstName | String | First Name
LastName | String | Last Name
Password | String | The Password
PhoneNumber | String | Phone Number
Role | String | User/Admin/SuperAdmin
Status | String | Active/InActive/Blocked
TwoFactorAuth | Object | TwoFactorAuth
TwoFactorAuth.Provider | String | Provider
TwoFactorAuth.SecretKey | String | SecretKey (Optional)
TwoFactorAuth.Enable | Boolean | Enable/Disable

<aside class="notice">
Notice
</aside>

- `TwoFactorAuth.Provider`
    - Fixed value: "google"


## User Login API

```shell
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/users/login"
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
        "Email": "sfs@gmail.com",
        "AccessToken":
          "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJJRCI6IjViYmQ0NzkzLTcxZDMtNDJjMS04MzM0LTg1MTdhODE3MTQxNiIsIkVtYWlsIjoiYmJiQGdtYWlsLmNvbSIsIlJvbGUiOiJVc2VyIiwiaWF0IjoxNTk0Mjk0MDI3fQ.KgoWredsavxn9_bvEG3CYhM_W5rLNCTZHqx2j7aWZMM",
        "RefreshToken":
          "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJJRCI6IjViYmQ0NzkzLTcxZDMtNDJjMS04MzM0LTg1MTdhODE3MTQxNiIsIkVtYWlsIjoiYmJiQGdtYWlsLmNvbSIsIlJvbGUiOiJVc2VyIiwiaWF0IjoxNTk0Mjk0MDMwfQ.b_92zLYwti4u5vbiBtkfZpuxszBJ9iWlSrTMLUmYraU",
      },
    ],
  }
```

Login endpoint, return access token and refresh token.

### HTTP Request

`POST https://fc-api.test.financecenter.sfs360.io/api/v1/users/login`

### Headers
Key | Value | Description
--------- | ------- | -----------
Content-Type | application/json | Content Type


### Body Parameters

Parameter | Type | Description
--------- | ------- | -----------
Email | String | Email Register
Password | String | The Password
OTP | String | OTP Code 

<aside class="notice">
Notice
</aside>

- `OTP`
    - Requied if TwoFactorAuth Is Enable



