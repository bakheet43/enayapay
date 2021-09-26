---
title: API Reference

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the EnayaPay API
---

# Introduction

Welcome to the EnayaPay API! You can use our API to access EnayaPay API endpoints.
# User Account Management
## Register

```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/register/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd"
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key.

### HTTP Request

`POST https://sandbox.enayapay.com/api/v2.1/register/`

### Description

`the use of this endpoint to register new user using phone number as id verification .`

### Headers
```json
 {
    "x-api-key": "fddfgdfgdfgdfgdfg"
  }

```
### Body
```json
 {
    "user_phone": "2499++++++++",
    "user_name": "doctor",
    "user_password": "calicofdhfdsfsd"
  }


```
### Parameters Description
Parameter | Default | Description | Type
--------- | ------- | ----------- | ----------
user_phone | required | user phone number | String
user_name | required | userName of user | String
user_password | required | user password | String


### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
201 | None | user created and otp will send in phone number
302 | None | user already registered
406 | `` {"details" : "your number not valid"} ``| phone number of user not valid
400 | `` { "details": {"user_password": [ "This field is required."]} } `` | Bad request occurred when forget parameter
502 | ```{"details" : "bad getway" }``` |  bad getway of sms getway
503 | ``` {"details" :"service not available"} ``` | when service not available


## verify

```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/verify/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd"
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key.

### HTTP Request

`POST https://sandbox.enayapay.com/api/v2.1/verify/`
### Description 

``the use of this endpoint to verification user phone number that he used``

### Headers
```json
 {
    "x-api-key": "fddfgdfgdfgdfgdfg"
  }

```
### Body
```json
 {
    "user_phone": "2499++++++++",
    "user_otp": "454345"
  }


```
### Parameters Description
Parameter | Default | Description | Type
--------- | ------- | ----------- | ----------
user_phone | required | user phone number | String
user_otp | required | otp of user | String


### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
200 | ``` {"token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IjU3NTMwNyIsImV4cGlyeSI6IjIwMjEtMTEtMTMifQ.2uU8eOnw8biYxH55EblrTHOz5nM4rcP1kiIa7S46mFs","user_name": "doctor"} ```| user verified
203 | None | wrong otp
400 | ``{ "details": {"user_otp": ["This field is required."]} }``| Bad request occurred when forget parameter 
401 | None | your api key not valid
404 | ``` {"details": "user not registered"} ``` | user not register
503 | ``` {"details" :"service not available"} ``` | when service not available


## login

```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/login/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd"
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key.


### HTTP Request
`POST https://sandbox.enayapay.com/api/v2.1/login/`

### Description

`` this endpoint use to access user account using password``

### Headers
```json
 {
    "x-api-key": "fddfgdfgdfgdfgdfg"
  }

```
### Body
```json
 {
    "user_phone": "2499++++++++",
    "user_password": "dfdfsdfdsfs"
  }


```
### Parameters Description
Parameter | Default | Description | Type
--------- | ------- | ----------- | ----------
user_phone | required | user phone number | String
user_password | required | password of user | String


### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
200 | ``` {"user_name": "doctor","status": "active"} ```| user authorized
203 | None | wrong password
400 | ``{ "details": {"user_password": ["This field is required."]} }``| Bad request occurred when forget parameter 
401 | None | your api key not valid
404 | ``` {"details": "user not registered"} ``` | user not register
503 | ``` {"details" :"service not available"} ``` | when service not available




## rest password

```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/rest/password/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd , token: ffdfdsfsdfds "
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key and Token.


### HTTP Request
`POST https://sandbox.enayapay.com/api/v2.1/rest/password/`

### Description

`` this endpoint use to rest user password when he forget``

### Headers
```json
 {
    "x-api-key": "fddfgdfgdfgdfgdfg",
    "token": "fsfsfkwoieriworiewriweiriwerieworioweir"
  }

```
### Body
```json
 {
    "user_phone": "2499++++++++",
    "user_password": "dfdfsdfdsfs"
  }


```
### Parameters Description
Parameter | Default | Description | Type
--------- | ------- | ----------- | ----------
user_phone | required | user phone number | String
user_password | required | password of user | String


### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
200 | ``` {"user_name": "doctor","status": "active"} ```| user rest his password successful
203 | None | not valid token
400 | ``{ "details": {"user_password": ["This field is required."]} }``| Bad request occurred when forget parameter 
401 | None | your api key not valid
404 | ``` {"details": "user not registered"} ``` | user not register
503 | ``` {"details" :"service not available"} ``` | when service not available


## change password

```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/change/password/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd , token: ffdfdsfsdfds "
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key and Token.


### HTTP Request
`POST https://sandbox.enayapay.com/api/v2.1/change/password/`

### Description

``this endpoint use to change user password that he used to access apllication .``

### Headers
```json
 {
    "x-api-key": "fddfgdfgdfgdfgdfg",
    "token": "fsfsfkwoieriworiewriweiriwerieworiowe"
  }

```
### Body
```json
 {
    "current_password": "gfgfdgdfg",
    "new_password": "dfdfsdfdsfs"
  }


```
### Parameters Description
Parameter | Default | Description | Type
--------- | ------- | ----------- | ----------
current_password | required | old password that user need to change | String
new_password | required | new_password that user need to change to it | String


### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
200 | ```{"details": "password updated successful"} ```| user changed his password successfully
203 | ``{"details": "wrong current password"}``| invalid old password
400 | ``{ "details": {"new_password": ["This field is required."]} }``| Bad request occurred when forget parameter 
401 | None | your api key not valid
404 | ``` {"details": "user not registered"} ``` | user not register
503 | ``` {"details" :"service not available"} ``` | when service not available

# Cards

## balance inquiry

```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/balance/inquiry/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd , token: ffdfdsfsdfds "
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key and Token.


### HTTP Request
`POST https://sandbox.enayapay.com/api/v2.1/balance/inquiry/`

### Description

``this endpoint use to provide information on the customer account balance``

### Headers
```json
 {
    "x-api-key": "fddfgdfgdfgdfgdfg",
    "token": "fsfsfkwoieriworiewriweiriwerieworiowe"
  }

```
### Body
```json
 {
    "pan":"45456789456798893",
    "ipin":"rtewrrtertretretrtrwtwrt",
    "uuid":"fdfregregergerlkfjerfklerjfkgerjgjre",
    "expiration_date":"0824"
  }


```
### Parameters Description
Parameter | Default | Description | Type
--------- | ------- | ----------- | ----------
pan | required | number of card that user want to known its balance | String
ipin | required | credential of customer | String
expiration_date | required | expiration  date of card| String
uuid | required | string



### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
200 | ```{"response_code": 0,"balance": 400,"response_status": "Successful","uuid": "fdfregregergerlkfjerfklerjfkgerjgjre"}```| account user informations
400 | ``{ "details": {"pan": ["This field is required."]} }``| Bad request occurred when forget parameter 
401 | None | your api key not valid
406 | ```{"response_code": 696,"response_message": "SYSTEM_ERROR"}``` | service provider errors with code
502 | ``` {"details" :"bad getway"} ``` | when service provider down 
