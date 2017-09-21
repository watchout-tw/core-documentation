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
| `name` | string | 用名稱過濾發言資料集 | partial | `罷` `罷免` |
| `term` | integer: term index | 用屆期過濾發言資料集 | exact | `8` `9` |
| `st` | integer: specific topic ID | 用關聯小議題過濾發言資料集 | exact | `1` `2` |
| `st_question` | integer: specific topic question ID | 用爭點過濾發言資料集 | exact | `1` `2` |
| `act` | integer: act ID | 用法案過濾發言資料集 | exact | `1` `2` |

### Response
```
{
  rows: [
    {
      id
      name
      version_no
      slug
      term_index
      start_date
      end_date
      st: {
        id
        title
        image
        index
      }
      st_question: {
        id
        question
      }
      acts: [
        {
          id
          title
          official_seq_no
        }
        ...
      ]
    }
    ...
  ]
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
  id
  name
  version_no
  slug
  term_index
  start_date
  end_date
  st_id
  st_question_id
  act_ids: [
    id
    ...
  ]
  should_have_spoken_committees: [
    name
    ...
  ]
  should_have_spoken_sessions: [
    index
    ...
  ]
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
| `act_ids` | array of integer | 法案 ID 列表 |
| `should_have_spoken_committees` | array of strings | 應發言委員會名稱列表 |
| `should_have_spoken_sessions` | array of integers | 應發言屆期 index |

### Sample input
```json
{
  "name": "罷免x第九屆",
  "version_no": "1.0.0",
  "slug": "bill-comp/recall/xxxx",
  "term_index": 9,
  "start_date": "2016-02-01 00:00:00",
  "end_date": "2020-01-31 00:00:00",
  "st_id": 1,
  "st_question_id": 1,
  "act_ids": [1, 2, 3],
  "should_have_spoken_committees": ["交通委員會", "內政委員會"],
  "should_have_spoken_sessions": [8, 9]
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
