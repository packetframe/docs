---
id: dns
title: DNS API
---

# DNS

#### List all DNS zones authorized for a user

`GET /dns/zones`

#### Example:

```bash
curl -X GET \
  -H "Authorization: Token <packetframe-api-token>" \
   https://packetframe.com/api/dns/zones
```

#### Add a new DNS zone

`POST /dns/zones`

| Name     | Description | Validation |
|----------|-------------|------------|
| zone     | DNS Zone    | Zone FQDN  |

#### Example:

```shell
curl -X POST \
  -H "Authorization: Token <packetframe-api-token>" \
  -H "Content-Type: application/json" \
  -d '{"zone": "example.com"}' \
  https://packetframe.com/api/dns/zones
```

#### Delete a DNS zone

`DELETE /dns/zones`

| Name | Description | Validation |
|------|-------------|------------|
| id   | Zone ID     |            |

#### Example:

```shell
curl -X DELETE \
  -H "Authorization: Token <packetframe-api-token>" \
  -H "Content-Type: application/json" \
  -d '{"id": "62244cdb-edb9-48ea-aeed-bad54bb70f9e"}' \
  https://packetframe.com/api/dns/zones
```

#### Add a user to a DNS zone

`PUT /dns/zones/user`

| Name | Description | Validation |
|------|-------------|------------|
| zone | Zone ID     |            |
| user | User email  |            |


#### Example:

```shell
curl -X PUT \
  -H "Authorization: Token <packetframe-api-token>" \
  -H "Content-Type: application/json" \
  -d '{"zone": "62244cdb-edb9-48ea-aeed-bad54bb70f9e", "user": "user1@example.com"}' \
  https://packetframe.com/api/dns/zones/user
```

#### Remove a user from a DNS zone

`DELETE /dns/zones/user`

| Name | Description | Validation |
|------|-------------|------------|
| zone | Zone ID     |            |
| user | User email  |            |

#### Example:

```shell
curl -X DELETE \
  -H "Authorization: Token <packetframe-api-token>" \
  -H "Content-Type: application/json" \
  -d '{"zone": "62244cdb-edb9-48ea-aeed-bad54bb70f9e", "user": "user1@example.com"}' \
  https://packetframe.com/api/dns/zones/user
```

#### List DNS records for a zone

`GET /dns/records/:id`

| Name | Description | Validation |
|------|-------------|------------|
| zone | Zone ID     |            |
| user | User email  |            |

#### Example:

```shell
curl -X DELETE \
  -H "Authorization: Token <packetframe-api-token>" \
  -H "Content-Type: application/json" \
  -d '{"zone": "62244cdb-edb9-48ea-aeed-bad54bb70f9e", "user": "user1@example.com"}' \
  https://packetframe.com/api/dns/zones/user
```

#### Add a DNS record to a zone

`POST /dns/records`

| Name    | Description                   | Validation                                                                          |
|---------|-------------------------------|-------------------------------------------------------------------------------------|
| zone    | Zone ID                       |                                                                                     |
| type    | Record Type                   | ("A", "AAAA", "CNAME", "TXT", "MX", "SRV", "NS", "SCRIPT") and part of valid record |
| label   | Record Label                  | Less than 255 characters and part of valid record                                   |
| value   | Record Value                  | Part of valid record                                                                |
| ttl     | Time To Live                  | Greater than 0 and part of valid record                                             |

#### Example:

```shell
curl -X POST \
  -H "Authorization: Token <packetframe-api-token>" \
  -H "Content-Type: application/json" \
  -d '{"zone": "62244cdb-edb9-48ea-aeed-bad54bb70f9e", "label": "@", "type": "A", "value": "192.0.2.1", "ttl": 300}' \
  https://packetframe.com/api/dns/records
```

#### Delete a DNS record from a zone

`DELETE /dns/records`

| Name   | Description  | Validation                                                                          |
|--------|--------------|-------------------------------------------------------------------------------------|
| zone   | Zone ID      |                                                                                     |
| record | Record ID    |                                                                                     |

#### Example:

```shell
curl -X DELETE \
  -H "Authorization: Token <packetframe-api-token>" \
  -H "Content-Type: application/json" \
  -d '{"zone": "62244cdb-edb9-48ea-aeed-bad54bb70f9e", "id": "967e3a9e-abb3-4bf0-87b8-d03bed13c95f"}' \
  https://packetframe.com/api/dns/records
```

#### Update a DNS record

`PUT /dns/records`

| Name  | Description  | Validation                                                                          |
|-------|--------------|-------------------------------------------------------------------------------------|
| zone  | Zone ID      |                                                                                     |
| id    | Record ID    |                                                                                     |
| type  | Record Type  | ("A", "AAAA", "CNAME", "TXT", "MX", "SRV", "NS", "SCRIPT") and part of valid record |
| label | Record Label | Less than 255 and part of valid record                                              |
| value | Record Value | Part of valid record                                                                |
| ttl   | Time To Live | Greater than 0 and part of valid record                                             |

#### Example:

```shell
curl -X PUT \
  -H "Authorization: Token <packetframe-api-token>" \
  -H "Content-Type: application/json" \
  -d '{"zone": "62244cdb-edb9-48ea-aeed-bad54bb70f9e", "id": "967e3a9e-abb3-4bf0-87b8-d03bed13c95f", "label": "@", "type": "A", "value": "192.0.2.1", "ttl": 300}' \
  https://packetframe.com/api/dns/records
```
