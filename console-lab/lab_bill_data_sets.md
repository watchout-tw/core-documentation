# Bill Data Sets

- [List bill data sets](#list-bill-data-sets)
- [Get a single bill data set](#get-a-single-bill-data-set)
- [Create a bill data set](#create-a-bill-data-set)
- [Update a bill data set](#update-a-bill-data-set)
- [Delete a bill data set](#delete-a-bill-data-set)

## List bill data sets
```
GET /console/lab/lab_bill_data_sets
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `st` | integer: specific topic ID | 用關聯小議題過濾提案資料集 | exact | `1` `2` |
| `act` | integer: act ID | 用法案過濾提案資料集 | exact | `1` `2` |
| `act_dir` | integer: act direction ID | 用修法方向過濾提案資料集 | exact | `1` `2` |

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
      act: {
        id,
        title,
        official_seq_no
      },
      act_dir: {
        id,
        name
      }
    },
    ...
  ],
  totalRowCount
}
```

## Get a single bill data set
```
GET /console/lab/lab_bill_data_sets/:id
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
  st_id,
  act_id,
  act_dir_id,
  act_feature_ids: [
    id,
    ...
  ],
  bill_ids: [
    id,
    ...
  ],
  scores: TBD...
}
```

## Create a bill data set
```
POST /console/lab/lab_bill_data_set
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
| `act_id` | integer | 關聯法案 ID |
| `act_dir_ids` | array of integers | 關聯修法方向 ID |
| `bill_ids` | array of integers | 提案 ID |
| `scores` | array of objects | 提案評分 |

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
  "act_id": 1,
  "act_dir_id": 2,
  "act_feature_ids": [1, 2, 3],
  "bill_ids": [21, 29, 33, 36],
  "scores": [
    {
      "bill_id": 21,
      "score_per_act_feature": [
        {
          "score": 1,
          "act_feature_id": 3
        },
        ...
      ]
    },
    ...
  ]
}
```

### Response
> Returns the newly created bill data set

## Update a bill data set
```
PATCH /console/lab/lab_bill_data_set/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create a bill data set](#create-a-bill-data-set)

## Delete a bill data set
```
DELETE /console/lab/lab_bill_data_set/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
