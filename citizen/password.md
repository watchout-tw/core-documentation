# Citizen’s password

- [Update password](#update-password)
- [Request reset password](#request-reset-password)
- [Reset password](#reset-password)

## Update password
```
PATCH /citizen/password
```

| Auth | Paging |
| :---: | :---: |
| 🌕 `citizen` | 🌑 |

## Request reset password
```
POST /citizen/request_reset_password
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

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

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

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
