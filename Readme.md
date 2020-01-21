<h1 align="center">Welcome to Rock Shop 👋</h1>
<p>
  <img src="https://img.shields.io/badge/version-1.0.0-blue.svg?cacheSeconds=2592000" />
</p>

![](/image/logo.png)

## Description

https://drive.google.com/file/d/1SAkY1Qyb5ThbOJXg7R8nlZivb31H49fq/view?usp=sharing

![API_Gateway](https://github.com/vinhyenvodoi98/rock_shop_microservice/blob/master/DocsImages/gateway.png)

## Auth_service

Tech requirements: nodejs + express + jwt + mongodb

### Main idea

Create UserSchema

When user register -> generate token -> create account

The tokens is saved as an array because the user who logs on in a new device will create a new token and then add it to the array so it won't affect any token on another device.

### API contact

- `HTTP POST /users — Register users.`
- `HTTP POST /users/login — Allow users to login.`
- `HTTP GET / users/me — Get user profile.`
- `HTTP POST /users/logout —Logout the user`
- `HTTP POST /users/logoutall — Logout from all devices.`

#### POST /users

**Input**

```json
[
  { "key": "email", "value": "testsss@gmail.com", "description": "" },
  { "key": "password", "value": "123456", "description": "" },
  { "key": "name", "value": "do hoang", "description": "" }
]
```

**Output**

```json
{
  "user": {
    "_id": "5e265dcadba4490279e3590d",
    "email": "testss@gmail.com",
    "name": "do hoang"
  },
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1ZTI2NWRjYWRiYTQ0OTAyNzllMzU5MGQiLCJpYXQiOjE1Nzk1NzI2ODN9.kBWyELerbvcfTFnaMDHTkdOvLDHU6ZJj2lf7rVEc9bM"
}
```

#### POST /users/login

**Input**

```json
[
  { "key": "email", "value": "testsss@gmail.com", "description": "" },
  { "key": "password", "value": "123456", "description": "" },
  { "key": "name", "value": "do hoang", "description": "" }
]
```

**Output**

```json
{
  "user": {
    "_id": "5e265dcadba4490279e3590d",
    "email": "testss@gmail.com",
    "name": "do hoang"
  },
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1ZTI2NWRjYWRiYTQ0OTAyNzllMzU5MGQiLCJpYXQiOjE1Nzk1NzI2ODN9.kBWyELerbvcfTFnaMDHTkdOvLDHU6ZJj2lf7rVEc9bM"
}
```

#### GET / users/me

**Input**

```json
[
  {
    "key": "Authorization",
    "value": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1ZTI2NWJiY2Y5MzM3MTAyMzNkNmY0OGIiLCJpYXQiOjE1Nzk1NzM1ODZ9.oeGqf8naFCEdJ2-SwDobYz_Ph7C_512KsOQAxmqmBos",
    "description": ""
  }
]
```

**Output**

```json
{
  "user": {
    "_id": "5e2662d7e24fd402cc0d33e0",
    "email": "testsss@gmail.com",
    "name": "do hoang"
  }
}
```

#### POST /users/me/logout

**Input**

```json
[
  {
    "key": "Authorization",
    "value": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1ZTI2NjJkN2UyNGZkNDAyY2MwZDMzZTAiLCJpYXQiOjE1Nzk1NzM5OTh9.KRy_NK8sl-iucVaTFZtweY50sRZHChOnNONI0BQkxaI",
    "description": ""
  }
]
```

**Output**

```json
{
  "success": true,
  "msg": "logout successfully"
}
```

#### POST /users/me/logoutall

**Input**

```json
[
  {
    "key": "Authorization",
    "value": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1ZTI2NjJkN2UyNGZkNDAyY2MwZDMzZTAiLCJpYXQiOjE1Nzk1NzQwNTJ9.rFAikyNlWL_e79DnXOGv2q5XNZ6paRfPc_-9YsgTIKc",
    "description": ""
  }
]
```

**Output**

```json
{
  "success": true,
  "msg": "logout all device successfully"
}
```
