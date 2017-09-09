# c0ngress/caucuses

## List caucuses
```
GET /c0ngress/caucuses
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `name` | string | 用姓名過濾黨團清單 | partial | `無` `民` |

### Response
```
{
  rows: [
    {
      id
      name
      abbreviation
      color
      emblem
      basic_info
      add_info
      type
      status
    }
    ...
  ],
  totalRowCount
}
```
