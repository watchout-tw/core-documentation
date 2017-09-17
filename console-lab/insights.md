# Insights

- [List insights](#list-insights)
- [Get a single insight](#get-a-single-insight)
- [Create a insight](#create-a-insight)
- [Update a insight](#update-a-insight)
- [Delete a insight](#delete-a-insight)

## List insights
```
GET /console/lab/lab_insights
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `st` | integer: specific topic ID | 用關聯小議題過濾分析評論 | exact | `1` `2` |
| `doc` | integer: document ID | 用文件過濾分析評論 | exact | `1` `2` |

### Response
```
{
  rows: [
    {
      id,
      status,
      slug,
      image,
      st: {
        id,
        title,
        image,
        index
      }
    }
    ...
  ],
  totalRowCount
}
```

## Get a single insight
```
GET /console/lab/lab_insight/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```
{
  id,
  status,
  slug,
  image,
  st: {
    id,
    title,
    image,
    index
  },
  doc: {
    TBD...
  }
}
```

## Create a insight
```
POST /console/lab/lab_insight
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |
| `status` | string | 狀態 |
| `slug` | string | 短網址 |
| `image` | string | 圖像的路徑 |
| `title` | integer | 標語 |
| `st_id` | integer | 關聯小議題 ID |

### Sample input
```json
{
  "status": "active",
  "slug": "http://goog.le/UH7bh8nsk",
  "image": "",
  "title": "數據分析報告",
  "st_id": 1
}
```

### Response
> Returns the newly created insight

## Update a insight
```
PATCH /console/lab/lab_insight/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create a insight](#create-a-insight)

## Delete a insight
```
DELETE /console/lab/lab_insight/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
