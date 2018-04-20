# Citizen’s password

- [Update password](#update-password)
- [Request reset password](#request-reset-password)
- [Reset password](#reset-password)

## Update password

```
PATCH /citizen/password
```

### Auth

- “citizen” AND “self”

### Input

| Key | Type | Required | Description |
| --- | --- | --- | --- |
| `password` | string | 🌕 | current citizen password |
| `new_password` | string | 🌕 | new citizen password |

### Sample input

```json
{
  "password":"12345",
  "new_password":"AAbb1234"
}
```

### Response

#### Wrong current password

``` json
{
  "statusCode": 400,
  "error": "Bad Request",
  "message": "WRONG_CITIZEN_PASSWORD"
}
```

#### Change password succedded

``` json
{
  "message": "SUCCEDDED"
}
```

## Request reset password

```
POST /citizen/request_reset_password
```

### Auth

NO

### Input

| Key | Type | Required | Description |
| --- | --- | --- | --- |
| `email` | string | 🌕 | Email |

### Sample input

```json
{
  "email": "a@b.com"
}
```

## Reset password
```
POST /citizen/reset_password
```

### Auth

NO

### Paging

NO

### Input

| Key | Type | Required | Description |
| --- | --- | --- | --- |
| `new_password` | string | 🌕 | 新的密碼 |

### Sample input
```json
{
  "new_password": "sEcr1t"
}
```
