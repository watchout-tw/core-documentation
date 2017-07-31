# Statement (rep speech)

- [List statements](#list-statements)
- [Get a single statement](#get-a-single-statement)
- [Create a statement](#create-a-statement)
- [Update a statement](#update-a-statement)
- [Delete a statement](#delete-a-statement)

## List statements
```
GET /console/lab/rs_statements
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌕 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `page` | integer | 頁次 | exact | `1` |
| `all` | - | 要求所有委員發言的清單 | - | - |
| `term` | integer: term index | 用屆期過濾委員發言清單 | exact | `8`,`9` |
| `rep` | integer: rep ID | 用發言委員過濾委員發言清單 | `1`,`2` |
| `rep_party` | integer: party ID | 用發言委員當時所屬政黨過濾委員發言清單 | `1`,`2` |
| `position` | string: directories.rs_position | 用立場過濾委員發言清單 | `pro`, `against`, `ambiguous` |

### Response
```
{
  rows: [
    {
      id,
      st: {
        id,
        title
      },
      date,
      term_index,
      session_index,
      rep: {
        id,
        name
      },
      rep_party: {
        id,
        name,
        abbreviation,
        color,
        emblem
      },
      content,
      position,
      position_summary
    }
    ...
  ],
  totalRowCount,
  paging: {
    page,
    pages,
    pageSize,
    previous,
    next
  }
}
```

## Get a single statement
```
GET /console/lab/rs_statements/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Response
```
{
  id,
  st_id,
  date,
  term_index,
  session_index,
  temp_session_index,
  rep_id,
  rep_party_id,
  principle_committee,
  joint_committees: [str, ...],
  content,
  st_question_id,
  position,
  position_summary,
  source_link,
  tags: [int, ...]
}
```

## Create a statement
```
POST /console/lab/rs_statements
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |
| `st_id` | integer | 關聯小議題 ID |
| `date` | timestamp | 日期 |
| `term_index` | integer | 屆期 |
| `session_index` | integer | 會期 |
| `temp_session_index` | integer | 臨時會期 |
| `rep_id` | integer: rep ID | 委員 |
| `rep_party_id` | integer: party ID | 委員當時所屬政黨 ID |
| `principle_committee` | string: committee name | 主審委員會 |
| `joint_committees` | array of strings: committee names | 聯席委員會名稱清單 |
| `content` | string | 內容 |
| `st_question_id` | integer: st_question ID | 爭點 ID |
| `position` | string: directories.rs_position | 立場 |
| `position_summary` | string | 立場摘要 |
| `source_link` | string | 原始資料連結 |
| `tags` | array of integers: tag IDs | 標籤 ID 清單 |

### Sample input
```json
{
  "st_id": 1,
  "date": 1498838400000,
  "term_index": 9,
  "session_index": 1,
  "temp_session_index": 2,
  "rep_id": 42,
  "rep_party_id": 3,
  "principle_committee": "司法及法治委員會",
  "joint_committees": [
    "財政委員會",
    "教育及文化委員會"
  ],
  "content": "Lorem ipsum.",
  "st_question_id": 2,
  "position": "pro",
  "position_summary": "Lorem ipsum.",
  "source_link": "https://something.gov.tw/path/to/source",
  "tags": [
    2, 4, 12
  ]
}
```

### Response
> Returns the newly created statement

## Update a statement
```
PATCH /console/lab/rs_statements/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create a statement](#create-a-statement)

## Delete a statement
```
DELETE /console/lab/rs_statements/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
