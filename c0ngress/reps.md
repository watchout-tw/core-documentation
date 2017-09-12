# c0ngress/reps

## List reps
```
GET /c0ngress/reps
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `name` | string | 用姓名過濾委員名單 | partial | `陳` `陳阿草` |

### Response
```
{
  rows: [
    {
      id
      name
    }
    ...
  ],
  totalRowCount
}
```
