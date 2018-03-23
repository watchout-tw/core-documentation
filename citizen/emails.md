# Citizen’s emails

- [Get emails of a citizen](#get-citizens-emails)
- [Add an email to a citizen](#add-an-email-to-a-citizen)
- [Delete an email from a citizen](#delete-an-email-from-a-citizen)
- [Request verification](#request-verification)
- [Confirm verification](#confirm-verification)
- [Set visibility](#set-visibility)
- [Set primary email](#set-primary-email)

## Get emails of a citizen
```
GET /citizen/:handle/emails
```

### Auth
- “citizen”

### Paging
NO

### Response
```
{
  rows: [
    {
      id
      email
      is_primary
      is_verified
      visibility
    }
  ]
  totalRowCount
}
```

## Add an email to a citizen
```
POST /citizen/:handle/emails
```

### Auth
- “citizen”

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | --- | --- |
| `email` | string | 🌕 | 要新增的email |

### Sample input
```json
{
  "email":"watchout@gmail.com"
}
```

## Delete a email from a citizen

```
DELETE /citizen/:handle/emails
```

### Auth
- “citizen”

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | --- | --- |
| `email` | string | 🌕 | 要刪除的email |

### Sample input
```json
{
  "email":"watchout@gmail.com"
}
```

## Request verification
```
GET /citizen/:handle/emails/:emailID/request_verification
```

### Auth
- “citizen”

### Paging
NO

## Confirm verification
```
GET /citizen/:handle/emails/:emailID/confirm_verification/:token
```

### Auth
- “citizen”

### Paging
NO

## Set visibility
```
PATCH /citizen/:handle/emails/:emailID/visibility
```

### Auth
- “citizen”

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | --- | --- |
| `visibility` | string | 🌕 | 要新增的email |

### Sample input
```json
{
  "email":"watchout@gmail.com"
}
```

## Set primary email
```
PATCH /citizen/:handle/emails/:emailID/set_primary
```

### Auth
- “citizen”

### Paging
NO
