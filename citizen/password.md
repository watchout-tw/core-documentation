# Citizen’s password

- [Request reset password](#request-reset-password)
- [Reset password](#reset-password)
- [Update password](#update-password)

## Request reset password
```
POST /citizen/request_reset_password
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |
| `email` | string | **Required.** Email |

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
| 🌕 | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |
| `new_password` | string | **Required.** 新的密碼 |

### Sample input
```json
{
  "new_password": "sEcr1t"
}
```

## Update password
```
PATCH /citizen/:handle/password
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |
