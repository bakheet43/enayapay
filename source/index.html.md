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
### Description
the use of this endpoint to register new user using phone number as id verification .
```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/register/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd"
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key.

### HTTP Request

`POST https://sandbox.enayapay.com/api/v2.1/register/`
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
333 | `` {"details" : "your number not valid"} ``| phone number of user not valid
400 | `` { "details": {"user_password": [ "This field is required."]} } `` | Bad request occurred when forget parameter
502 | ```{"details" : "bad getway" }``` |  bad getway of sms getway
503 | ``` {"details" :"service not available"} ``` | when service not available


## verify
### Description
the use of this end point to verify user phone number .
```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/verify/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd"
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key.

### HTTP Request

`POST https://sandbox.enayapay.com/api/v2.1/verify/`
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
### Description
the use of this endpoint used to access user account by use it's password . 
```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/login/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd"
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key.

### HTTP Request
`POST https://sandbox.enayapay.com/api/v2.1/login/`

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
200 | ``` {"token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IjU3NTMwNyIsImV4cGlyeSI6IjIwMjEtMTEtMTMifQ.2uU8eOnw8biYxH55EblrTHOz5nM4rcP1kiIa7S46mFs","user_name": "doctor","status": "active"} ```| user authorized
203 | None | wrong password
400 | ``{ "details": {"user_password": ["This field is required."]} }``| Bad request occurred when forget parameter 
401 | None | your api key not valid
404 | ``` {"details": "user not registered"} ``` | user not register
503 | ``` {"details" :"service not available"} ``` | when service not available
