# User API Spec

## Register User

Endpoint : POST /api/users

Request Body :

```json
{
    "username": "fadhli",
    "password": "123",
    "name": "Muhammad Fadhli Al Hafizh"
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
    "errors" : "Username already registered"
}
```

## Login User

Endpoint : POST /api/auth/login

Request Body :

```json
{
    "username": "fadhli",
    "password": "123"
}
```

Response Body (Success) :

```json
{
    "data" : {
        "token": "TOKEN",
        "expiredAt": 1232435342 // miliseconds
    }
}
```

Response Body (Failed, 401) :

```json
{
    "errors" : "Username or password wrong"
}
```

## Get User

Endpoint : GET /api/users/current

Request Header : 

- X-API-TOKEN : Token (Mandatory)

Response Body (Success) :

```json
{
    "data" : {
        "username": "fadhli",
        "name": "Muhammad Fadhli Al Hafizh"
    }
}
```

Response Body (Failed, 401) :

```json
{
    "errors" : "Unauthorized"
}
```

## Update User

Endpoint : PATCH /api/users/current

Request Header : 

- X-API-TOKEN : Token (Mandatory)

Request Body :

```json
{
    "name": "fadhli", // put if only want to update name
    "password": "new password" // put if only want to update password
}
```

Response Body (Success) :

```json
{
    "data" : {
        "username": "fadhli",
        "name": "Muhammad Fadhli Al Hafizh"
    }
}
```

Response Body (Failed, 401) :

```json
{
    "errors" : "Username already used by another user"
}
```


## Logout User

Endpoint : DELETE /api/auth/logout

Request Header : 

- X-API-TOKEN : Token (Mandatory)

Response Body (Success) :

```json
{
    "data": "OK"
}
```