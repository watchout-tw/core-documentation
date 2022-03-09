# tags

- [List tags](#list-tags)
- [Get a single tag](#get-a-single-tag)
- [Create a tag](#create-a-tag)
- [Update a tag](#update-a-tag)
- [Delete a tag](#delete-a-tag)

## List tags
```
GET /comp/tags
```

### Auth
- “editor”

### Paging
NO

### Available query parameters
NO

### Response
```
{
  rows: [
    {
      id
      slug
      title
      description
      data
    }
    ...
  ]
}
```

## Get a single by slug
```
GET /comp/tags/:slug
```

### Auth
- “editor”

### Paging
NO

### Response
```
{
  id
  slug
  title
  description
  data
}
```

## Create a tag
```
POST /comp/tags
```

### Auth
- “editor”

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `slug` | string | 🌕 | 標籤的短網址 |
| `title` | string | 🌕 | 標籤的標題 |
| `description` | string | 🌕 | 標籤的敘述 |
| `data` | object | 🌑 | 其它任何需要紀錄在此標籤的資料（非必要不使用） |

### Sample input
```json
{
  "slug": "event-one",
  "title": "沃草的第一個事件",
  "description": "其它必要的敘述",
  "data": **JSON**
}
```

### Response
> Returns the newly created tag

## Update a tag
```
PATCH /comp/tags/:id
```

### Auth
- “editor”

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `id` | integer | 🌕 | 標籤 ID |
| `slug` | string | 🌕 | 標籤的短網址 |
| `title` | string | 🌕 | 標籤的標題 |
| `description` | string | 🌕 | 標籤的敘述 |
| `data` | object | 🌑 | 其它任何需要紀錄在此標籤的資料（非必要不使用） |

### Sample input
```json
{
  "id": 1,
  "slug": "event-one",
  "title": "沃草的第一個事件",
  "description": "其它必要的敘述",
  "data": **JSON**
}
```

## Delete a tag
```
DELETE /comp/tags/:id
```

### Auth
- “editor”

### Paging
NO

### Response
```javascript
204 No Content
```
