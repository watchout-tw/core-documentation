# Vote (rep speech)

- [List votes](#list-votes)
- [Get a single vote](#get-a-single-vote)
- [Create a vote](#create-a-vote)
- [Update a vote](#update-a-vote)
- [Delete a vote](#delete-a-vote)

## List votes
```
GET /console/lab/votes
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌕 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `page` | integer | 頁次 | exact | `1` |
| `all` | - | 要求所有委員表決的清單 | - | - |
| `st` | integer: specific topic ID | 用關聯小議題過濾委員表決清單 | exact | `1`,`2` |
| `term` | integer: term index | 用屆期過濾委員表決清單 | exact | `8`,`9` |

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
      title,
      aye_count,
      abstain_count,
      nay_count,
      absence_count,
      g0v_link,
      source_link
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

## Get a single vote
```
GET /console/lab/votes/:id
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
  title,
  content,
  aye: [int, ...],
  nay: [int, ...],
  abstain: [int, ...],
  absence: [int, ...],
  g0v_link,
  source_link,
  tags: [int, ...]
}
```

## Create a vote
```
POST /console/lab/votes
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |
| `st_id` | integer: specific topic ID | 關聯小議題 ID |
| `date` | timestamp | 日期 |
| `term_index` | integer | 屆期 |
| `session_index` | integer | 會期 |
| `temp_session_index` | integer | 臨時會期 |
| `title` | string | 標題 |
| `content` | string | 內容 |
| `aye` | array of integers: rep IDs | 贊成委員 ID 清單 |
| `nay` | array of integers: rep IDs | 反對委員 ID 清單 |
| `abstain` | array of integers: rep IDs | 棄權委員 ID 清單 |
| `absence` | array of integers: rep IDs | 缺席委員 ID 清單 |
| `g0v_link` | string | 公民科技社群連結 |
| `source_link` | string | 原始資料連結 |
| `tags` | array of integers: tag IDs | 標籤 ID 清單 |

### Sample input
```json
{
  "st_id": 6,
  "date": 1498838400000,
  "term_index": 9,
  "session_index": 1,
  "temp_session_index": 2,
  "title": "Lorem ipsum.",
  "content": "Lorem ipsum.",
  "aye": [
    2, 3, 4, 6, 8, 14, 42
  ],
  "nay": [
    1, 5, 9, 64, 96
  ],
  "abstain": [
    7, 8, 10, 11, 12, 13
  ],
  "absence": [
    15, 16, 24, 101
  ],
  "g0v_link": "https://g0v.tw/path/to/page",
  "source_link": "https://something.gov.tw/path/to/source",
  "tags": [
    2, 4, 12
  ]
}
```

### Response
> Returns the newly created vote

## Update a vote
```
PATCH /console/lab/votes/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create a vote](#create-a-vote)

## Delete a vote
```
DELETE /console/lab/votes/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
