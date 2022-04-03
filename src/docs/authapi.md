---
id: auth
title: Authentication API
---

# Authentication

#### Log a user in

`POST /user/login`

| Name     | Description           | Validation          |
|----------|-----------------------|---------------------|
| email    | User's email address  | Email address       |
| password | User's password       | Min 10 characters   |

#### Example:

```bash
curl -X POST \
  -H "Content-Type: application/json" \
  -d '{"email": "user1@example.com", "password": "your-password"}' \
  https://packetframe.com/api/user/login
```

#### Create a new user account

`POST /user/signup`

| Name     | Description                           | Validation        |
|----------|---------------------------------------|-------------------|
| email    | User's email address                  | Email address     |
| password | User's password                       | Min 10 characters |
| ref      | Where did you hear about Packetframe? |                   |

#### Example:

```bash
curl -X POST \
  -H "Content-Type: application/json" \
  -d '{"email": "user1@example.com", "password": "your-password", "ref": "Nate"}' \
  https://packetframe.com/api/user/signup
```

#### Delete a user account

`DELETE /user/delete`

#### Example:

```bash
curl -X DELETE \
  -H "Authorization: Token <packetframe-api-token>" \
  https://packetframe.com/api/user/delete
```

#### Change a user's password

`POST /user/password`

| Name     | Description  | Validation             |
|----------|--------------|------------------------|
| password | New password | At least 10 characters |

#### Example:

```bash
curl -X POST \
  -H "Authorization: Token <packetframe-api-token>" \
  -H "Content-Type: application/json" \
  -d '{"password": "new-password"}' \
  https://packetframe.com/api/user/password
```

#### Get user info

`GET /user/info`

#### Example:

```bash
curl -X GET \
  -H "Authorization: Token <packetframe-api-token>" \
  https://packetframe.com/api/user/info
```
