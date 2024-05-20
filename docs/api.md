# RESTful API docs

## Authorization

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

## User

`GET http://HOST:PORT/user/me` - return currently authorized user profile

Auth: `Bearer Token`

Response:
```json
{
    "user": {
        "id": 1,
        "uuid": "7c5f07dd-be3e-443d-9bee-709401150caf",
        "username": "username",
        "fullname": "Full Name",
        "email": "email@email.com",
        "password": "$argon2id$v=19$m=65536,t=10,p=4$fkhoQ0z6kJfH+uZAMq1lkg$p/bGqyQW1/kGsDHhSJwWQp5uFGjty5eUwVKeFIJbbcw",
        "createdAt": "2024-05-10T14:23:43.991Z",
        "updatedAt": "2024-05-18T21:53:32.070Z"
    }
}
```

`GET http://HOST:PORT/user/{username}` - return profile of the user by it's username

Auth: `Bearer Token`

Response:
```json
{
  "user": {
    "id": 2,
    "uuid": "4bd3fdcb-221f-482f-bf09-d81cfc9dbc38",
    "username": "username1",
    "fullname": "Full Name",
    "email": "email1@email.com",
    "password": "$argon2id$v=19$m=65536,t=10,p=4$wqu2W8YBE2PBu1rNicn8Ew$H94hfq6gqlNSAMp+PQ6QzaBw9IDVRm7J7+zGvl7Y/MA",
    "createdAt": "2024-05-19T14:49:31.193Z",
    "updatedAt": "2024-05-19T14:49:31.193Z"
  }
}
```

`PATCH http://HOST:PORT/user/me` - update user data

Auth: `Bearer Token`

Body:
```json
{
    "username": "new uesrname",
    "fullname": "New FullName"
}
```

Response:
```json
{
    "id": 1,
    "uuid": "7c5f07dd-be3e-443d-9bee-709401150caf",
    "username": "new uesrname",
    "fullname": "New FullName",
    "email": "email@email.com",
    "password": "$argon2id$v=19$m=65536,t=10,p=4$fkhoQ0z6kJfH+uZAMq1lkg$p/bGqyQW1/kGsDHhSJwWQp5uFGjty5eUwVKeFIJbbcw",
    "createdAt": "2024-05-10T14:23:43.991Z",
    "updatedAt": "2024-05-20T09:48:53.227Z"
}
```

## Post
`GET http://HOST:PORT/posts` - get all posts

Auth: `Bearer Token`

Response:
```json
{
    "posts": [
        {
            "id": 1,
            "uuid": "b292bbfb-4ee9-4a5f-b31e-3f0f2fcec3d9",
            "title": "first post",
            "content": "this is content of the my first post in student hub",
            "userId": "7c5f07dd-be3e-443d-9bee-709401150caf",
            "rating": 0,
            "votes": null,
            "createdAt": "2024-05-19T16:24:00.822Z",
            "updatedAt": "2024-05-19T16:24:00.822Z"
        },
        {
            "id": 2,
            "uuid": "acd52d63-cecb-46d0-886c-fe4962b17654",
            "title": "first post",
            "content": "this is content of the my first post in student hub",
            "userId": "7c5f07dd-be3e-443d-9bee-709401150caf",
            "rating": 0,
            "votes": null,
            "createdAt": "2024-05-19T16:27:07.018Z",
            "updatedAt": "2024-05-19T16:27:07.018Z"
        },
        {
            "id": 3,
            "uuid": "33c94a0a-bb56-45e2-9895-561a43347d4a",
            "title": "First post",
            "content": "It is a content of my first post",
            "userId": "7c5f07dd-be3e-443d-9bee-709401150caf",
            "rating": 0,
            "votes": null,
            "createdAt": "2024-05-20T09:51:35.979Z",
            "updatedAt": "2024-05-20T09:51:35.979Z"
        }
    ]
}
```

`GET http://HOST:PORT/posts/{post_id}` - get post by it's uuid

Auth: `Bearere Token`

Response:
```json
{
    "post": {
        "id": 3,
        "uuid": "33c94a0a-bb56-45e2-9895-561a43347d4a",
        "title": "First post",
        "content": "It is a content of my first post",
        "userId": "7c5f07dd-be3e-443d-9bee-709401150caf",
        "rating": 0,
        "votes": null,
        "createdAt": "2024-05-20T09:51:35.979Z",
        "updatedAt": "2024-05-20T09:51:35.979Z"
    }
}
```

`POST http://HOST:PORT/posts` - creates a new post

Auth: `Bearer Token`

Body: 
```json
{
    "title": "First post",
    "content": "It is a content of my first post"
}
```

Response:
```json
{
    "post": {
        "id": 3,
        "uuid": "33c94a0a-bb56-45e2-9895-561a43347d4a",
        "userId": "7c5f07dd-be3e-443d-9bee-709401150caf",
        "title": "First post",
        "content": "It is a content of my first post",
        "rating": 0,
        "updatedAt": "2024-05-20T09:51:35.979Z",
        "createdAt": "2024-05-20T09:51:35.979Z"
    }
}
```

`PATCH http://HOST:PORT/posts/{post_id}` - update posts contents or rating

**Update content**

Auth: `Bearer Token`

Body: 
```json
{
    "title": "new post title",
    "content": "It is an updated content of my first post"
}
```

Response:
```json
{
    "post": {
        "id": 3,
        "uuid": "33c94a0a-bb56-45e2-9895-561a43347d4a",
        "userId": "7c5f07dd-be3e-443d-9bee-709401150caf",
        "title": "new post title",
        "content": "It is an updated content of my first post",
        "rating": 0,
        "updatedAt": "2024-05-20T09:51:35.979Z",
        "createdAt": "2024-05-20T09:51:35.979Z"
    }
}
```

**Rate post**

Auth: `Bearer Token`

Body:

```json
{
  "rating": 100
}
```

Response:
```json
{
    "post": {
        "id": 3,
        "uuid": "33c94a0a-bb56-45e2-9895-561a43347d4a",
        "userId": "7c5f07dd-be3e-443d-9bee-709401150caf",
        "title": "new post title",
        "content": "It is an updated content of my first post",
        "rating": 100,
        "updatedAt": "2024-05-20T09:51:35.979Z",
        "createdAt": "2024-05-20T09:51:35.979Z"
    }
}
```

`DELETE http://HOST:PORT/posts/{post_id}` - delete post

Auth: `Bearer Token`

Response:

```json
{
  "message": "Post has been deleted".
}
```
