# Invoice verification 載具驗證

- [Carruer verification](#carruer-verification)
- [Lovecode verification](#lovecode-verification)

## Carruer verification 電子載具驗證

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

## Lovecode verification 愛心碼驗證
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