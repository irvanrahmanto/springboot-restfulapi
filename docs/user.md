# User API Spec

## Register User

Endpoint: POST /api/users
Request Body :

```json
{
  "username" : "admin",
  "password" : "root",
  "name" : "John Doe"
}
```

Response Body (Success) :
```json
{
  "data" : "OK"
}
```

Response Body (Failed) :
```json
{
  "errors": "Username must not blank, ???"
}
```

## Login User

Endpoint: POST /api/auth/login
- Request Body :

```json
{
  "username" : "admin",
  "password" : "password"
}
```

- Response Body (Success) :
```json
{
  "data" : {
    "token" : "TOKEN",
    "expiredAt" : 12393128908932 // milliseconds
  }
}
```

- Response Body (Failed, 401) :
```json
{
  "errors": "Username or password wrong"
}
```
## Get user

Endpoint: GET /api/users/current

Request Header :
- X-API-TOKEN : Token (Mandatory)

Response Body (Success) :
```json
{
  "data" : {
    "username" : "john",
    "name" : "john doe"
  }
}
```

Response Body (Failed, 401) :
```json
{
  "errors": "Unauthorized"
}
```

## Update User

Endpoint: PATCH /api/users/current

Request Header :
- X-API-TOKEN : Token (Mandatory)

Request Body :

```json
{
  "name" : "john doe", // put if only want to update name
  "password" : "new password" // put if only want to update password
}
```

Response Body (Success) :
```json
{
  "data" : {
    "username" : "john",
    "name" : "john doe"
  }
}
```

Response Body (Failed, 401) :
```json
{
  "errors": "Unauthorized"
}
```

## Logout User

Endpoint: DELETE /api/auth/logout

Request Header :
- X-API-TOKEN : Token (Mandatory)

Response Body (Success) :
```json
{
  "data" : "OK"
}
```