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
| `term` | integer | 屆期 | exact | `8`,`9` |
| `rep` | integer: rep ID | 發言委員 ID | `1`,`2` |
| `rep_party` | integer: party ID | 發言委員當時所屬政黨 ID | `1`,`2` |
| `position` | string: directories.rs_position | 立場 | `pro`, `against`, `ambiguous` |

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
