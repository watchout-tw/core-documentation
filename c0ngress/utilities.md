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
GET /c0ngress/date_to_term
```

### Auth
NO

### Paging
NO

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
> 使用 timestamp 及委員 ID 列表查詢委員們在該時刻的政黨、黨團、委員會等資訊

```
GET /c0ngress/date_to_rep_info
```

### Auth
NO

### Paging
NO

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `date` | timestamp | **Required.** The date to lookup. | exact | `1498838400000` |
| `reps` | array of integers: rep IDs | **Required.** The reps to lookup. | exact | [1] or [1,2,3] |

### Response
```json
{
  "reps": [
    {
      "id": 1,
      "name": "陳阿草",
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
      ]
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
GET /c0ngress/zones
```

### Auth
NO

### Paging
NO

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
> 取得某個屆期之中不重複的會期編號

```
GET /c0ngress/unique_sessions
```

### Auth
NO

### Paging
NO

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `term` | integer: term index | **Required.** The term to lookup. | exact | `8` `9` |

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
> 取得某個屆期之中不重複的臨時會期編號，也可以進一步限制到某個會期中的臨時會期

```
GET /c0ngress/unique_temp_sessions
```

### Auth
NO

### Paging
NO

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `term` | integer: term index | **Required.** The term to lookup. | exact | `8` `9` |
| `session` | integer | Optional. The session to lookup. This session must exist within the term defined above. | exact | `1` `2` |

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
GET /c0ngress/unique_districts
```

### Auth
NO

### Paging
NO

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
> 取得系統中所有政府單位的清單

```
GET /c0ngress/gov_agencies
```

### Auth
NO

### Paging
NO

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
> 取得系統定義的所有立法步驟

```
GET /c0ngress/legislative_steps
```

### Auth
NO

### Paging
NO

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
