# timelines

- [List timelines](#list-timelines)
- [Get a single timeline](#get-a-single-timeline)
- [Create a timeline](#create-a-timeline)
- [Update a timeline](#update-a-timeline)
- [Delete a timeline](#delete-a-timeline)

## List timelines
```
GET /comp/timelines
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
      title
      description
      data
      editor
      create_date
      update_date
    }
    ...
  ]
}
```

## Get a single timeline
```
GET /comp/timelines/:id
```

### Auth
- “editor”

### Paging
NO

### Response
```
{
  id
  title
  description
  data
  editor
  create_date
  update_date
}
```

## Create a timeline
```
POST /comp/timelines
```

### Auth
- “editor”

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `title` | string | 🌕 | 時間軸標題 |
| `description` | string | 🌕 | 時間軸敘述 |
| `data` | json | 🌑 | 其它任何需要紀錄在此時間軸的資料（非必要不使用） |
| `authors` | array of persona ids | 🌕 | 此時間軸的作者們 Persona ID |
| `tags` | array of tag ids | 🌕 | 此時間軸的 Tag |

### Sample input
```json
{
  "title": "沃草大紀事",
  "description": "沃草的種種",
  "authors": [1, 2, 3],
  "tags": [1, 2],
  "data": **JSON**
}
```

### Response
> Returns the newly created timeline

## Update a timeline
```
PATCH /comp/timelines/:id
```

### Auth
- “editor”

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `id` | integer | 🌕 | 時間軸 ID |
| `title` | string | 🌕 | 時間軸標題 |
| `description` | string | 🌕 | 時間軸敘述 |
| `data` | json | 🌑 | 其它任何需要紀錄在此時間軸的資料（非必要不使用） |
| `authors` | array of persona ids | 🌕 | 此時間軸的作者們 Persona ID |
| `tags` | array of tag ids | 🌕 | 此時間軸的 Tag |

### Sample input
```json
{
  "id": 1,
  "title": "沃草大紀事",
  "description": "沃草的種種",
  "data": **JSON**,
  "authors": [1, 2, 3],
  "tags": [1, 2]
}
```

## Delete a timeline
```
DELETE /comp/timelines/:id
```

### Auth
- “editor”

### Paging
NO

### Response
```javascript
204 No Content
```
