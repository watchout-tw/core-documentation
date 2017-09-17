# Statement Data Sets

- [List statement data sets](#list-statement-data-sets)
- [Get a single statement data set](#get-a-single-statement-data-set)
- [Create a statement data set](#create-a-statement-data-set)
- [Update a statement data set](#update-a-statement-data-set)
- [Delete a statement data set](#delete-a-statement-data-set)

## List statement data sets
```
GET /console/lab/lab_statement_data_sets
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `st` | integer: specific topic ID | 用關聯小議題過濾發言資料集 | exact | `1` `2` |
| `st_question` | integer: specific topic question ID | 用爭點過濾發言資料集 | exact | `1` `2` |

### Response
```
{
  rows: [
    {
      id,
      name,
      version_no,
      term_index,
      st: {
        id,
        title,
        image,
        index
      },
      st_question: {
        id,
        question
      },
      acts: [
        {
          id,
          title,
          official_seq_no
        },
        ...
      ]
    },
    ...
  ],
  totalRowCount
}
```

## Get a single statement data set
```
GET /console/lab/lab_statement_data_sets/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```
{
  id,
  name,
  version_no,
  slug,
  term_index,
  start_date,
  end_date,
  st: {
    id,
    title,
    image,
    index
  },
  st_question: {
    id,
    question
  },
  acts: [
    {
      id,
      title,
      official_seq_no
    },
  ],
  should_have_spoken_committees: {
    name,
    abbreviation,
    category
  },
  should_have_sopken_sessions: {
    session_index,
    temp_session_index,
    start_date,
    end_date
  }
}
```

## Create a statement data set
```
POST /console/lab/lab_statement_data_set
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |
| `name` | string | 名稱 |
| `version_no` | string | 版本號 |
| `slug` | string | 短網址 |
| `term_index` | integer | 屆期 |
| `start_date` | timestamp | 起始日 |
| `end_date` | timestamp | 終止日 |
| `st_id` | integer | 關聯小議題 ID |
| `st_question_id` | integer | 爭點 ID |
| `should_have_spoken_committees` | integer | 應發言委員會 ID |
| `should_have_spoken_sessions` | integer | 應發言屆期 |

### Sample input
```json
{
  "name": "罷免x第九屆",
  "version_no": "1.0.0",
  "slug": "http://goog.le/UH7bh8nsk",
  "term_index": 9,
  "start_date": "2016-02-01 00:00:00",
  "end_date": "2020-01-31 00:00:00",
  "st_id": 1,
  "st_question_id": 1,
  "should_have_spoken_committees": 2,
  "should_have_spoken_sessions": 9
}
```

### Response
> Returns the newly created statement data set

## Update a statement data set
```
PATCH /console/lab/lab_statement_data_set/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create a statement data set](#create-a-statement-data-set)

## Delete a statement data set
```
DELETE /console/lab/lab_statement_data_set/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
