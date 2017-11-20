# Timeline Events

- [List timeline events](#list-timeline-events)
- [Get a single timeline event](#get-a-single-timeline-events)
- [Create a timeline event](#create-a-timeline-events)
- [Update a timeline event](#update-a-timeline-events)
- [Delete a timeline event](#delete-a-timeline-events)

## List timeline events
```
GET /console/comp/timeline_events
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌕 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `date` | timestamp | 用日期來過濾大事紀事件清單 | exact | `1498838400000` |
| `type` | string | 用類型來過濾大事紀事件清單 | exact | `general_update` `data_reports` |
| `q` | string | 用關鍵字對標語（tagline）、標題（title）、內容（content）來過濾大事紀事件清單 | partial | `建` `建國` |

### Response
```
{
  rows: [
    {
      status,
      slug,
      date,
      type,
      image,
      tagline,
      title,
      content,
      link,
      data
    }
    ...
  ],
  totalRowCount
}
```

## Get a single timeline event
```
GET /console/comp/timeline_events/:id
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
  date,
  type,
  image,
  tagline,
  title,
  content,
  link,
  data
}
```

## Create a timeline event
```
POST /console/comp/timeline_events
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `status` | string | 🌕 | 狀態 |
| `slug` | string | 🌕 | 短網址 |
| `date` | timestamp | 🌕 | 日期 |
| `type` | string | 🌕 | 類型 |
| `image` | string | 🌑 | 圖像 |
| `tagline` | string | 🌑 | 標語 |
| `title` | string | 🌕 | 標題 |
| `content` | string | 🌑 | 內容 |
| `link` | string | 🌑 | 連結 |
| `data` | object | 🌑 | 與此事件相關之資料 |

### Sample input
```json
{
  "status": "active",
  "slug": "bill-comp/recall/xxxx",
  "date": 1498838400000,
  "type": "基本",
  "image": "path/image.png",
  "tagline": "體育選手只能相忍為國？",
  "title": "打開黑箱協會的第一步",
  "content": "關於台灣獨立與台灣建國",
  "link": "https://g0v.tw",
  "data": **JSON**
}
```

### Response
> Returns the newly created timeline event

## Update a timeline event
```
PATCH /console/comp/timeline_events/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create a timeline event](#create-a-timeline-event)

## Delete a timeline event
```
DELETE /console/lab/timeline_events/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
