# Utilities

- [Date to term](#date-to-term)
- [Zones](#zones)
- [District unique names](#district-unique-names)
- [Government agencies](#government-agencies)
- [Legislative steps](#legislative-steps)

## Date to term
> 使用 timestamp 查詢該時刻是落在哪一個屆期、會期、臨時會期之中

```
GET /console/lab/date_to_term
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `date` | timestamp | The timestamp to lookup. | in range | `1498838400000` |

### Response
```javascript
{
  term_index,
  session_index,
  temp_session_index,
  start_date,
  end_date,
  date,
}
```
## Zones
> 取得區域名稱；區域是選區的上層結構

```
GET /console/lab/zones
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Response
```javascript
{
  rows: [
    {
      name,
      abbreviation,
      category
    }
    /* ... */
  ],
  totalRowCount
}
```

## District unique names
> 取得系統中所有不重複的選區名稱

```
GET /console/lab/district_unique_names
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Response
```javascript
{
  rows: [
    {
      name
    }
    /* ... */
  ],
  totalRowCount
}
```

## Government agencies
```
GET /console/lab/gov_agencies
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Response
```javascript
{
  rows: [
    {
      id,
      name
    }
    /* ... */
  ],
  totalRowCount
}
```

## Legislative steps
```
GET /console/lab/legislative_steps
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Response
```javascript
{
  rows: [
    {
      id,
      name
    }
    /* ... */
  ],
  totalRowCount
}
```
