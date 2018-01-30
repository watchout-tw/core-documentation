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

| Auth | Paging |
| :---: | :---: |
| 🌕 `citizen` | 🌑 |

### Response
```
{
  rows: [
    {
      emailID
      email
      visibility
      is_primary
    }
  ]
  totalRowCount
}
```

## Add an email to a citizen
```
POST /citizen/:handle/emails
```

| Auth | Paging |
| :---: | :---: |
| 🌕 `citizen` | 🌑 |

### Input

| Key | Type | Required | Description |
| --- | --- | --- | --- |
| `email` | string | 🌕 | 要新增的email |

## Delete a email from a citizen
```
DELETE /citizen/:handle/emails
```

| Auth | Paging |
| :---: | :---: |
| 🌕 `citizen` | 🌑 |

## Request verification
```
GET /citizen/:handle/emails/:emailID/request_verification
```

| Auth | Paging |
| :---: | :---: |
| 🌕 `citizen` | 🌑 |

## Confirm verification
```
GET /citizen/:handle/emails/:emailID/confirm_verification/:token
```

| Auth | Paging |
| :---: | :---: |
| 🌕 `citizen` | 🌑 |

## Set visibility
```
PATCH /citizen/:handle/emails/:emailID/visibility
```

| Auth | Paging |
| :---: | :---: |
| 🌕 `citizen` | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |

## Set primary email
```
PATCH /citizen/:handle/emails/:emailID/set_primary
```

| Auth | Paging |
| :---: | :---: |
| 🌕 `citizen` | 🌑 |
