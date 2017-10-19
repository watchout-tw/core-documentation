# Timelines

- [List timelines](#list-timelines)
- [Get a single timeline](#get-a-single-timeline)
- [Create a timeline](#create-a-timeline)
- [Update a timeline](#update-a-timeline)
- [Delete a timeline](#delete-a-timeline)

## List timelines
```
GET /console/lab/timelines
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `title` | string | 用標題過濾大事紀 | partial | `建` `建國` |

### Response
```
{
  rows: [
    {
      id,
      status,
      type,
      title
    }
    ...
  ],
  totalRowCount
}
```

## Get a single timeline
```
GET /console/lab/timeline/:id
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
  title,
  description,
  event_ids: [
    id
    ...
  ]
}
```

## Create a timeline
```
POST /console/lab/timeline
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |
| `status` | string | 狀態 |
| `slug` | string | 短網址 |
| `type` | string | 類型 |
| `image` | string | 圖像的路徑 |
| `title` | string | 標題 |
| `description` | string | 敘述 |
| `events` | array of objects | 事件 |

### Sample input
```json
{
  "status": "active",
  "slug": "bill-comp/recall/xxxx",
  "type": "基本",
  "image": "path/image.png",
  "title": "台灣建國大世紀",
  "description": "關於台灣獨立與台灣建國",
  "events": [
    {
      "status": "active",
      "slug": "bill-comp/recall/xxxx",
      "date": "2014-01-01",
      "type": "基本",
      "image": "path/image.png",
      "tagline": "體育選手只能相忍為國？",
      "title": "打開黑箱協會的第一步",
      "content": "關於台灣獨立與台灣建國"
    }
  ]
}
```

### Response
> Returns the newly created timeline

## Update a timeline
```
PATCH /console/lab/timeline/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create a timeline](#create-a-timeline)

## Delete a timeline
```
DELETE /console/lab/timeline/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
