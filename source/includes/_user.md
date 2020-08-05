# User

## User Registration API

```shell
curl --location --request POST 'https://fc-api.test.financecenter.sfs360.io/api/v1/users/register' \
--header 'Content-Type: application/json' \
--data-raw '{
    "Email": "user@sfs360.io",
    "Password": "Password",
    "ConfirmPassword": "Password",
    "FirstName": "John",
    "LastName": "Doe",
    "DisplayName": "John Doe",
    "Status": "Active",
    "Role": "Admin",
    "Country": "NL",
    "PhoneNumber": "+31638319078",
    "TwoFactorAuth": {
        "Provider": "google",
        "Enable": true
    }
}'
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
          "ID": "90875c91-7899446-462676-9e908802-59b887c6f",
          "Email": "user@sfs360.io",
          "Role": "Admin",
          "Status": "Active",
          "Country": "NL",
          "DisplayName": "John Doe",
          "Name": {
              "FirstName": "John",
              "LastName": "Doe"
          },
          "PhoneNumber": "+31638319078",
          "TwoFactorAuth": {
            "Provider": "google",
            "Enable": true
          }
      }
  ]
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
Email | String | Email Register
Password | String | Password
ConfirmPassword | String | Confirm Password
FirstName | String | First Name
LastName | String | Last Name
DisplayName | String | Display Name
Password | String | The Password
Status | String | Active/InActive/Blocked
Role | String | User/Admin/SuperAdmin
Country | String | Country (ISO land code)
PhoneNumber | String | Phone Number
TwoFactorAuth | Object | TwoFactorAuth
TwoFactorAuth.Provider | String | Provider
TwoFactorAuth.Enable | Boolean | Enable/Disable

<aside class="notice">
Notice
</aside>

- `TwoFactorAuth.Provider`
    - Fixed value: "google"


## User Login API

```shell
curl --location --request POST 'https://fc-api.test.financecenter.sfs360.io/api/v1/users/login' \
--header 'Content-Type: application/json' \
--data-raw '{
    "Password": "Password",
    "Email": "user@sfs360.io",
    "OTP": "123456"
}'
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
        "Email": "user@sfs360.io",
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



