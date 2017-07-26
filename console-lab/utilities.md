# Utilities

## Date to term
> 使用 timestamp 查詢該時刻是落在哪一個屆期、會期、臨時會期之中

```
GET /console/lab/date_to_term
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `date` | timestamp | The timestamp to lookup. | in range | `1498838400000` |

### Response
``` js
{
  term_index,
  session_index,
  temp_session_index,
  start_date,
  end_date,
  date,
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
``` js
{
  rows: [
    {
      name
    }
    ...
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
``` js
{
  rows: [
    {
      id,
      name
    }
    ...
  ],
  totalRowCount
}
```
