---
id: api
---

# Authentication

### API Reference:

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

# DNS

### API Reference:

#### Add a zone

`POST /zones`

Required parameters:

| Name     | Description | Validation    |
|----------|-------------|---------------|
| zone     | DNS Zone    | Zone          |

Example response (HTTP 200):

```json
{
  "message": "Zone added"
}
```

#### Get records

`GET /zones/:zone/records`

Example response (HTTP 200):

```json
[
  {
    "id": "606baec834665f846c7f3e30",
    "type": "A",
    "label": "@",
    "value": "192.0.2.1",
    "ttl": 300,
    "proxied": false
  }
]
```

#### Add a record

`POST /zones/:zone/records`

Required parameters:

| Name    | Description                   | Validation                                                                |
|---------|-------------------------------|---------------------------------------------------------------------------|
| zone    | ID of zone to add record to   |                                                                           |
| type    | DNS RR Type                   | ("A", "AAAA", "CNAME", "TXT", "MX", "SRV", "NS") and part of valid record |
| label   | DNS RR Label                  | Less than 255 and part of valid record                                    |
| value   | DNS RR Value                  | Part of valid record                                                      |
| ttl     | Time To Live                  | Greater than 0 and part of valid record                                   |
| proxied | Should the record be proxied? |                                                                           |

Example response (HTTP 200):

```json
{
  "message": "Record added"
}
```

#### Delete a record

`DELETE /zones/:zone/records/:record`

Example response (HTTP 200):

```json
{
  "message": "Record added"
}
```

#### Update a record

`PATCH /zones/:zone/records`

Required parameters:

| Name    | Description                   | Validation                                                                |
|---------|-------------------------------|---------------------------------------------------------------------------|
| zone    | ID of zone to add record to   |                                                                           |
| type    | DNS RR Type                   | ("A", "AAAA", "CNAME", "TXT", "MX", "SRV", "NS") and part of valid record |
| label   | DNS RR Label                  | Less than 255 and part of valid record                                    |
| value   | DNS RR Value                  | Part of valid record                                                      |
| ttl     | Time To Live                  | Greater than 0 and part of valid record                                   |
| proxied | Should the record be proxied? |                                                                           |

Example response (HTTP 200):

```json
{
  "message": "Record updated"
}
```

# Edge

### API Reference:

#### Create a container

`POST /containers`

Required parameters:

| Name     | Description                          | Validation          |
|----------|--------------------------------------|---------------------|
| image    | Docker image path                    |                     |
| ports    | List of port map entries ("80:8080") | "uint16:uint16"     |
| env      | Environment map (string to string)   |                     |

Example response (HTTP 200):

```json
{
  "message": "Container created"
}
```

### Delete a container

`DELETE /containers/:container`

Required parameters: None

Example response (HTTP 200):

```json
{
  "message": "Container deleted"
}
```
