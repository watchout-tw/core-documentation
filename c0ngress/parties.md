# Party
> 政黨

## List parties
```
GET /c0ngress/parties
```

### Auth
NO

### Paging
NO

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `name` | string | 用姓名過濾政黨清單 | partial | `無` `民` |

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
    }
    ...
  ]
  totalRowCount
}
```
