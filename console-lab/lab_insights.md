# Insights

- [List insights](#list-insights)
- [Get a single insight](#get-a-single-insight)
- [Create a insight](#create-a-insight)
- [Update a insight](#update-a-insight)
- [Delete a insight](#delete-a-insight)

## List insights
```
GET /console/lab/insights
```

### Auth
- “editor”

### Paging
NO

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
GET /console/lab/insight/:id
```

### Auth
- “editor”

### Paging
NO

### Response
```
{
  id,
  status,
  slug,
  image,
  st_id,
  doc_id
}
```

## Create a insight
```
POST /console/lab/insight
```

### Auth
- “editor”

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `status` | string | 🌕 | 狀態 |
| `slug` | string | 🌑 | 短網址 |
| `image` | string | 🌑 | 圖像的路徑 |
| `title` | integer | 🌕 | 標語 |
| `st_id` | integer | 🌕 | 關聯小議題 ID |
| `doc_id` | integer | 🌑 | 文件 ID |

### Sample input
```json
{
  "status": "active",
  "slug": "bill-comp/recall/xxxx",
  "image": "path/image.png",
  "title": "數據分析報告",
  "st_id": 1,
  "doc_id": 3
}
```

### Response
> Returns the newly created insight

## Update a insight
```
PATCH /console/lab/insight/:id
```

### Auth
- “editor”

### Paging
NO

> 參考 [Create a insight](#create-a-insight)

## Delete a insight
```
DELETE /console/lab/insight/:id
```

### Auth
- “editor”

### Paging
NO

### Response
```javascript
204 No Content
```
