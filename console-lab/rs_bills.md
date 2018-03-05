# Bill (rep speech)

- [List bills](#list-bills)
- [Get a single bill](#get-a-single-bill)
- [Create a bill](#create-a-bill)
- [Update a bill](#update-a-bill)
- [Delete a bill](#delete-a-bill)

## List bills
```
GET /console/lab/rs_bills
```

### Auth
- “editor”

### Paging
YES

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `page` | integer | 頁次 | exact | `1` |
| `all` | - | 要求所有委員提案的清單 | - | - |
| `st` | integer: specific topic ID | 用關聯小議題過濾委員提案清單 | exact | `1` `2` |
| `act` | integer: act ID | 用關聯法案過濾委員提案清單 | exact | `1` `2` |
| `term` | integer: term index | 用屆期過濾委員提案清單 | exact | `8` `9` |
| `principle_sponsor_type` | string: directories.principle_sponsor_type | 用第一提案人類別過濾委員提案清單 | exact | `gov_agency` `caucus` `rep` |
| `principle_sponsor_value` | integer: gov agency/caucus/rep ID | 用第一提案人過濾委員提案清單 | exact | `1` `2` |
| `principle_sponsor_party` | integer: party ID | 用第一提案人政黨過濾委員提案清單 | `4` `6` |

### Response
```
{
  rows: [
    {
      id
      specific_topics: [
        {
          id
          title
        }
        ...
      ]
      act: {
        id
        title
      }
      is_law
      version_no
      date
      term_index
      session_index
      principle_sponsor_type
      principle_sponsor_value: {
        id
        name
      }
      principle_sponsor_parties: [
        {
          id
          name
          abbreviation
          color
          emblem
        }
        ...
      ]
    }
    ...
  ]
  totalRowCount
  paging: {
    page
    pages
    pageSize
    previous
    next
  }
}
```

## Get a single bill
```
GET /console/lab/rs_bills/:id
```

### Auth
- “editor”

### Paging
NO

### Response
```
{
  id
  act_id
  is_law
  version_no
  date
  term_index
  session_index
  temp_session_index
  principle_sponsor_type
  principle_sponsor_value
  sponsors: [int, ...]
  cosponsors: [int, ...]
  content
  data_source_link
  progress_source_link
  tags: [int, ...]
  legislative_steps: [
    {
      date
      legislative_step_id
    }
    ...
  ]
  st_questions: [
    {
      st_id // 與樓下爭點（st_question_id）相關連的小議題 ID
      st_question_id
      position
    }
    ...
  ]
  act_features: [
    {
      st_id // 與樓下修法方向（act_dir_id）相關連的小議題 ID
      act_dir_id
      act_feature_id
      short_content
      content
    }
  ]
}
```

## Create a bill
```
POST /console/lab/rs_bills
```

### Auth
- “editor”

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `act_id` | integer: act ID | 🌕 | 關聯法案 ID |
| `is_law` | boolean | 🌕 | 是否為法律？ |
| `version_no` | string | 🌑 | 提案或法律版本號 |
| `date` | timestamp | 🌑 | 日期 |
| `term_index` | integer: term_index | 🌑 | 屆期 |
| `session_index` | integer | 🌑 | 會期 |
| `temp_session_index` | integer | 🌑 | 臨時會期 |
| `principle_sponsor_type` | string: directories.principle_sponsor_type | 🌑 | 第一提案人類別 |
| `principle_sponsor_value` | int: gov agency/caucus/rep ID | 🌑 | 第一提案人 |
| `sponsors` | array of integers: rep IDs | 🌑 | 提案委員 ID 清單 |
| `cosponsors` | array of integers: rep IDs | 🌑 | 連署委員 ID 清單 |
| `content` | string | 🌑 | 內容 |
| `data_source_link` | string | 🌑 | 資料來源連結 |
| `progress_source_link` | string | 🌑 | 進程來源連結 |
| `tags` | array of integers: tag IDs | 🌑 | 標籤 ID 清單 |
| `legislative_steps` **[1]** | array of objects | 🌑 | 審議進度物件清單 |
| `st_questions` **[2]** | array of objects | 🌑 | 爭點物件清單 |
| `act_features` **[3]** | array of objects | 🌕 | 法案比較物件清單 |

`[1]`

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| date | timestamp | 🌕 | 日期 |
| legislative_step_id | Integer | 🌕 | 審議進度 ID |

`[2]`

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| st_id | Integer | 🌕 | 小議題 ID |
| st_question_id | Integer | 🌕 | 爭點 ID |
| position | string | 🌕 | 立場 |

`[3]`

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| st_id | Integer | 🌕 | 小議題 ID |
| act_dir_id | Integer | 🌕 | 修法方向 ID |
| act_feature_id | Integer | 🌕 | 法案比較 ID |
| short_content | string | 🌕 | 簡短內容 |
| content | string | 🌕 | 完整內容 |

### Sample input
```json
{
  "act_id": 1,
  "is_law": false,
  "version_no": "18278",
  "date": 1498838400000,
  "term_index": 9,
  "session_index": 1,
  "temp_session_index": 2,
  "principle_sponsor_type": "rep",
  "principle_sponsor_value": 42,
  "sponsors": [
    1, 2, 3
  ],
  "cosponsors": [
    4, 5, 6
  ],
  "content": "Lorem ipsum",
  "data_source_link": "https://something.gov.tw/path/to/source",
  "progress_source_link": "https://something.gov.tw/path/to/source",
  "tags": [
    2, 4, 12
  ],
  "legislative_steps": [
    {
      "date": 1498838400000,
      "legislative_step_id": 1
    }
  ],
  "st_questions": [
    {
      "st_id": 1,
      "st_question_id": 1,
      "position": "pro"
    }
  ],
  "act_features": [
    {
      "act_dir_id": 1,
      "act_feature_id": 1,
      "short_content": "Lorem.",
      "content": "Lorem ipsum."
    }
  ]
}
```

### Response
> Returns the newly created bill

## Update a bill
```
PATCH /console/lab/rs_bills/:id
```

### Auth
- “editor”

### Paging
NO

> 參考 [Create a bill](#create-a-bill)

## Delete a bill
```
DELETE /console/lab/rs_bills/:id
```

### Auth
- “editor”

### Paging
NO

### Response
```javascript
204 No Content
```
