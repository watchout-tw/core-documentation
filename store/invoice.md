# Invoice verification

- [Carruer verification](#carruer-verification)
- [Lovecode verification](#lovecode-verification)

## Carruer verification
```
POST /store/carruer/verification
```

### Auth
NO

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `carruerNum` | string | 🌕 | 電子載具 |

### Sample input
```json
{
  "carruerNum": "/P7W3QO2"
}
```

### Response
```
204 No content
```

## Lovecode verification
```
POST /store/lovecode/verification
```

### Auth
NO

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `loveCode` | string | 🌕 | 愛心碼 |

### Sample input
```json
{
  "loveCode": "0096"
}
```

### Response
```
204 No content
```