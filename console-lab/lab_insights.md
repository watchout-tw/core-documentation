# Lab Insights

- [List lab insights](#list-lab-insights)
- [Get a single lab insight](#get-a-single-lab-insight)
- [Create a lab insight](#create-a-lab-insight)
- [Update a lab insight](#update-a-lab-insight)
- [Delete a lab insight](#delete-a-lab-insight)

## List lab insights
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

## Get a single lab insight
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

## Create a lab insight
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
> Returns the newly created lab insight

## Update a lab insight
```
PATCH /console/lab/lab_insight/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create a lab insight](#create-a-lab-insight)

## Delete a lab insight
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
