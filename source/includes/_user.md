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

Parameter | Type | Description | Required
--------- | ------- | ----------- | -
Email | String | Email Address | Yes
Password | String | Password | Yes
ConfirmPassword | String | Confirm Password | Yes
FirstName | String | First Name | Yes
LastName | String | Last Name | Yes
DisplayName | String | Display Name | Yes
Password | String | The Password | Yes
Status | String | Active/InActive/Blocked | Yes
Role | String | User/Admin/SuperAdmin | Yes
Country | String | Country (ISO land code) | Yes
PhoneNumber | String | Phone Number | Yes
TwoFactorAuth | Object | TwoFactorAuth | No
TwoFactorAuth.Provider | String | Provider | No *
TwoFactorAuth.Enable | Boolean | Enable/Disable | No *

<aside class="notice">
Notice
</aside>

- `TwoFactorAuth.Provider`
    + Fixed value: "google"
    + Mandatory if `TwoFactorAuth` is not empty
- `TwoFactorAuth.Enable`
    + Mandatory if `TwoFactorAuth` is not empty


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

Parameter | Type | Description | Required
--------- | ------- | ----------- | --
Email | String | Email Address | Yes
Password | String | Password | Yes
OTP | String | OTP Code | No *

<aside class="notice">
Notice
</aside>

- `OTP`
  + Required when `TwoFactorAuth` is Enabled



