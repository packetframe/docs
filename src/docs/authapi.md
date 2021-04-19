---
id: auth
title: Authentication API
---

# Authentication

#### Signup

`POST /signup`

Required parameters:

| Name     | Description           | Validation          |
|----------|-----------------------|---------------------|
| email    | User's email address  | Email address       |
| password | User's password       | Min 10 characters   |

Example response (HTTP 200):

```json
{
  "message": "Signup success"
}
```

#### Login

`POST /login`

Required parameters:

| Name     | Description           | Validation          |
|----------|-----------------------|---------------------|
| email    | User's email address  | Email address       |
| password | User's password       | Min 10 characters   |

Example response (HTTP 200):

```json
{
  "key": "Epk3Xq9X4dPvQjTjY3Odskx17EiiitVSvBTfwla0REC4AvcU"
}
```
