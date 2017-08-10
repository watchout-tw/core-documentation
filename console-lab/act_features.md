# Act Feature

- [List act features](#list-act-features)
- [Get a single act feature](#get-a-single-act-feature)
- [Create an act feature](#create-an-act-feature)
- [Update an act feature](#update-an-act-feature)
- [Delete an act feature](#delete-an-act-feature)

## List act features
```
GET /console/lab/act_features
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `st` | integer: specific topic ID | 用關聯小議題過濾法案比較清單 | exact | `1` `2` |
| `act` | integer: act ID | 用關聯法案過濾法案比較清單 | exact | `1` `2` |
| `act_dir` | integer: act dir ID | 用關聯修法方向過濾法案比較清單 | exact | `1` `2` |

### Response
```
{
  rows: [
    {
      id,
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
      },
      feature,
      dir
    }
    ...
  ],
  totalRowCount
}
```

## Get a single act feature
```
GET /console/lab/act_features/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```
{
  id,
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
  },
  feature,
  dir,
  content,
  scale_score_max,
  scale: [
    {
      score,
      description
    }
    ...
  ]
}
```

## Create an act feature
```
POST /console/lab/act_features
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |
| `st` | integer | 小議題 ID |
| `act` | integer | 法案 ID |
| `act_dir` | integer | 修法方向 ID |
| `feature` | string | 法案比較名稱 |
| `dir` | string | 法案比較價值判斷 |
| `content` | integer | 內容說明 |
| `scale_score_max` | integer | 量尺分數最大值 |
| `scale` | array of object | 量尺 |

### Sample input
```json
{
  "st": 1,
  "act": 2,
  "act_dir": 4,
  "feature": "提案門檻",
  "dir": "降低提案門檻",
  "content": "Lorem ipsum.",
  "scale_score_max": 5,
  "scale": [
    {
      "score": 1,
      "description": "0.5%"
    },
    {
      "score": 2,
      "description": "0.1%"
    },
    {
      "score": 3,
      "description": "0.05%"
    },
    {
      "score": 4,
      "description": "100人"
    },
    {
      "score": 5,
      "description": "刪除門檻"
    }
  ]
}
```

### Response
> Returns the newly created act feature

## Update an act feature
```
PATCH /console/lab/act_features/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create an act feature](#create-an-act-feature)

## Delete an act feature
```
DELETE /console/lab/act_features/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
