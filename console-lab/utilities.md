# Utilities

- [Date to term](#date-to-term)
- [Date to rep info](#date-to-rep-info)
- [Zones](#zones)
- [Unique sessions](#unique-sessions)
- [Unique temp sessions](#unique-temp-sessions)
- [Unique districts](#unique-districts)
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
| `date` | timestamp | **Required.** The timestamp to lookup. | in range | `1498838400000` |

### Response
```json
{
  "term_index": 8,
  "session_index": 1,
  "temp_session_index": 0,
  "start_date": "2017-06-14T00:00:08.000Z",
  "end_date": "2017-06-14T00:00:08.000Z",
  "date": "2017-06-14T00:00:08.000Z"
}
```

## Date to rep info
```
GET /console/lab/date_to_rep_info
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `date` | timestamp | **Required.** The date to lookup. | in range | `1498838400000` |
| `rep` | integer: rep ID | **Required.** The rep to lookup. | exact | `1`,`2` |

### Response
```json
{
  "party_id": 3,
  "caucus_id": 3,
  "committees": [
    {
      "name": "修憲委員會",
      "is_convener": true
    },
    {
      "name": "司法及法制委員會",
      "is_convener": false
    }
  ],
  "term_index": 8,
  "session_index": 1,
  "temp_session_index": 0,
  "start_date": "2017-06-14T00:00:08.000Z",
  "end_date": "2017-06-14T00:00:08.000Z",
  "date": "2017-06-14T00:00:08.000Z"
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
```json
{
  "rows": [
    {
      "name": "台南市",
      "abbreviation": "台南",
      "category": "直轄市"
    }
  ],
  "totalRowCount": 42
}
```

## Unique sessions
```
GET /console/lab/unique_sessions
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `term` | integer: term index | **Required.** The term to lookup. | exact | `8`,`9` |

### Response
```json
{
  "rows": [
    {
      "session_index": 1
    },
    {
      "session_index": 2
    }
  ],
  "totalRowCount": 42
}
```

## Unique temp sessions
```
GET /console/lab/unique_temp_sessions
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `term` | integer: term index | **Required.** The term to lookup. | exact | `8`,`9` |
| `session` | integer | Optional. The session to lookup. This session must exist within the term defined above. | exact | `1`,`2` |

### Response
```json
{
  "rows": [
    {
      "temp_session_index": 0
    },
    {
      "temp_session_index": 1
    }
  ],
  "totalRowCount": 42
}
```

## Unique districts
> 取得系統中所有不重複的選區名稱

```
GET /console/lab/unique_districts
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Response
```json
{
  "rows": [
    {
      "name": "台南市第一選區"
    }
  ],
  "totalRowCount": 42
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
```json
{
  "rows": [
    {
      "id": 1,
      "name": "行政院"
    }
  ],
  "totalRowCount": 42
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
```json
{
  "rows": [
    {
      "id": 6,
      "name": "三讀"
    }
  ],
  "totalRowCount": 42
}
```
