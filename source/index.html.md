---
title: SFS Finance Centre API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - javascript

toc_footers:
  # - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - creditor
  - debtor
  - errors
  - exact
  - invoice
  - invoice_expected
  - invoice_incoming
  - invoice_outgoing
  - search
  - user
  - xtendis

search: true

code_clipboard: true
---

# Introduction

Welcome to the SFS Finance Centre (FC) API! You can use our API to access SFS FC API endpoints, which can get information in our database.

We have language bindings in Shell and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

<aside class="success">
Additionally, We also deployed swagger docs https://fc-api.test.financecenter.sfs360.io/docs
</aside>
# Authentication
> To get token, use this code:

```shell
curl --location --request POST 'https://fc-api.test.financecenter.sfs360.io/api/v1/users/login' \
--header 'Content-Type: application/json' \
--data-raw '{
    "email": "test@test.com",
    "password": "p@ssw0rd"
}'
```

```javascript
var axios = require('axios');
var data = JSON.stringify({"email":"test@test.com","password":"p@ssw0rd"});

var config = {
  method: 'post',
  url: 'https://fc-api.test.financecenter.sfs360.io/api/v1/users/register',
  headers: { 
    'Content-Type': 'application/json'
  },
  data : data
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});

```
> The above command returns JSON structured like this:

```json
{
  "token": "token_xxx"
}
```
> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://fc-api.test.financecenter.sfs360.io/api/v1/{path}"
  -H "Authorization: token_xxx"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('token_xxx');
```

> Make sure to replace `token_xxx` with your API key.

SFS FC uses API keys to allow access to the API. Please contact to administrator to register an account.

SFS FC expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: token_xxx`

<aside class="notice">
You must replace <code>token_xxx</code> with your personal API key.
</aside>
