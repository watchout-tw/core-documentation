# Timeline Events

- [List timeline events](#list-timeline-events)
- [Get a single timeline event](#get-a-single-timeline-event)
- [Create a timeline event](#create-a-timeline-event)
- [Update a timeline event](#update-a-timeline-event)
- [Delete a timeline event](#delete-a-timeline-event)

## List timeline events
```
GET /comp/timelines/:timelineID/events
```

### Auth
- “editor”

### Paging
NO

### Response
```
{
  rows: [
    {
      title
      date
      description
      data
    }
    ...
  ]
  totalRowCount
}
```

## Get a single timeline event
```
GET /comp/timelines/:timelineID/event/:eventID
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
  date
  description
  data
}
```

## Create a timeline event
```
POST /comp/timelines/:timelineID/events
```

### Auth
- “editor”

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `title` | string | 🌕 | 標題 |
| `date` | timestamp | 🌕 | 日期 |
| `description` | string | 🌕 | 敘述 |
| `data` | object | 🌑 | 與此事件相關之資料（非必要不使用） |

### Sample input
```json
{
  "title": "2020 年黑克松",
  "date": 1498838400000,
  "description": "some information listed here",
  "data": **JSON**
}
```

### Response
> Returns the newly created timeline event

## Update a timeline event
```
PATCH /comp/timelines/:timelineID/events/:eventID
```

### Auth
- “editor”

### Paging
NO

> 參考 [Create a timeline event](#create-a-timeline-event)

## Delete a timeline event
```
DELETE /comp/timelines/:timelineID/events/:eventID
```
### Auth
- “editor”

### Paging
NO

### Response
```javascript
204 No Content
```
