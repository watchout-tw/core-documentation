# Rep

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
| `name` | string | 列出姓名中包含該字串的委員名單 | partial | `陳` `陳阿草` |
| `party` | integer: party ID | 列出**曾經屬於**該政黨的委員名單 | exact | `1` `2` |
| `start_date` | timestamp | 列出從該時間點起算至今**曾任**委員的名單 | less than | `1498838400000` |
| `end_date` | timestamp | 列出至該時間點為止**曾任**委員的名單 | greater than | `1498838400000` |
| `term` | integer: term index | 列出在該屆期中**曾任**委員的名單 | exact | `8` `9` |

> 以`term`查詢，則不可使用`start_date`或`end_date`，反之亦然。

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
