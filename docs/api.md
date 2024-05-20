# RESTful API docs

**Authorization**

`POST http://HOST:PORT/auth/signup` - Create user

Body:
```json
{
    "username": string,
    "fullname": string,
    "email": string,
    "password": string,
    "password_repeat": string
}
```

`POST http://HOST:PORT/auth/signin` - returns auth token for user

Body:
```json
{
    "email": string,
    "password": string
}
```

Response:
```json
{
  "token": string
}
```
