# Lab Topic Overviews

- [List topic overviews](#list-topic-overviews)
- [Get a single act feature](#get-a-single-topic-overview)
- [Create a topic overviews](#create-a-topic-overview)
- [Update a topic overviews](#update-a-topic-overview)
- [Delete a topic overviews](#delete-a-topic-overview)

## List topic overviews
```
GET /console/lab/lab_topic_overviews
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `st` | integer: specific topic ID | 用關聯小議題過濾議題綜覽 | exact | `1` `2` |
| `timeline` | integer: timeline ID | 用大事紀過濾議題綜覽 | exact | `1` `2` |

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
      },
      tagline,
      title,
      intro,
      description
    }
    ...
  ],
  totalRowCount
}
```

## Get a single topic overview
```
GET /console/lab/lab_topic_overview/:id
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
  tagline,
  title,
  intro,
  description,
  timeline: {
    id,
    status,
    slug,
    type,
    image,
    title,
    description,
    event: [
      {
        id,
        status,
        slug,
        type,
        image,
        title,
        description,
        link,
        data
      }
      ...
    ]
  },
  related_links
}
```

## Create a topic overview
```
POST /console/lab/lab_topic_overview
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
| `st_id` | integer | 關聯小議題 ID |
| `tagline` | string | 簡介 |
| `title` | integer | 標語 |
| `intro` | integer | 敘述 |
| `timeline_id` | integer | 大事紀 ID |
| `data_report_id` | integer | 大事紀 ID |
| `insight_id` | integer | 數據分析報告 ID |
| `related_links` | array of objects | 相關連結 |

### Sample input
```json
{
  "status": "active",
  "slug": "http://goog.le/UH7bh8nsk",
  "image": "",
  "st_id": 1,
  "tagline": "選賢與能，選錯了怎麼辦？",
  "title": "數據分析報告",
  "intro": "從歐巴馬這個例子，更加可以理解到，連美國人自己針對台灣問題也經常說不清楚。",
  "timeline_id": 1,
  "data_report_id": 2,
  "insight_id": 3,
  "related_links": [
    {
      "type": "???",
      "url": "http://abc.com.tw",
      "title": "???"
    }
    ...
  ]
}
```

### Response
> Returns the newly created topic overview

## Update a topic overview
```
PATCH /console/lab/lab_topic_overview/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create a topic overview](#create-a-topic-overview)

## Delete a topic overview
```
DELETE /console/lab/lab_topic_overview/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
