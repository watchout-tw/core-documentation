# Timelines

- [List timelines](#list-timelines)
- [Get a single timeline](#get-a-single-timeline)
- [Create a timeline](#create-a-timeline)
- [Update a timeline](#update-a-timeline)
- [Delete a timeline](#delete-a-timeline)

## List timelines
```
GET /console/comp/timelines
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
GET /console/comp/timelines/:id
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
POST /console/comp/timelines
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `status` | string | 🌕 | 狀態 |
| `slug` | string | 🌑 | 短網址 |
| `type` | string | 🌕 | 類型 |
| `image` | string | 🌑 | 圖像的路徑 |
| `title` | string | 🌕 | 標題 |
| `description` | string | 🌑 | 敘述 |
| `event_ids` | array of integers: Timeline_Event IDs | 🌑 | 大事紀事件 ID 列表 |

### Sample input
```json
{
  "status": "active",
  "slug": "bill-comp/recall/aXj0Q",
  "type": "基本",
  "image": "path/image.png",
  "title": "台灣建國大世紀",
  "description": "關於台灣獨立與台灣建國",
  "event_ids": [
    1,
    2,
    3
  ]
}
```

### Response
> Returns the newly created timeline

## Update a timeline
```
PATCH /console/comp/timelines/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create a timeline](#create-a-timeline)

## Delete a timeline
```
DELETE /console/lab/timelines/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
