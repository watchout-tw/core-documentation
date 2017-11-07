# Topic Overview

- [List topic overviews](#list-topic-overviews)
- [Get a single topic overview](#get-a-single-topic-overview)
- [Create a topic overview](#create-a-topic-overview)
- [Update a topic overview](#update-a-topic-overview)
- [Delete a topic overview](#delete-a-topic-overview)

## List topic overviews
```
GET /console/lab/topic_overviews
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `st` | integer: specific topic ID | 用關聯小議題過濾議題綜覽 | exact | `1` `2` |
| `title` | string | 用標題過濾議題綜覽 | partial | `罷` `罷免` |

### Response
```
{
  rows: [
    {
      id
      status
      slug
      image
      st: {
        id
        title
        image
        index
      }
      tagline
      title
      intro
      description
    }
    ...
  ]
  totalRowCount
}
```

## Get a single topic overview
```
GET /console/lab/topic_overview/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```
{
  id
  status
  slug
  image
  st_id
  tagline
  title
  intro
  description
  timeline_id
  related_links
}
```

## Create a topic overview
```
POST /console/lab/topic_overview
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `status` | string | 🌕 | 狀態 |
| `slug` | string | 🌑 | 短網址 |
| `image` | string | 🌕 | 圖像的路徑 |
| `st_id` | integer | 🌕 | 關聯小議題 ID |
| `tagline` | string | 🌕 | 標語 |
| `title` | string | 🌕 | 標題 |
| `intro` | string | 🌕 | 簡介 |
| `description` | string | 🌕 | 敘述 |
| `timeline_id` | integer | 🌕 | 大事紀 ID |
| `related_links` **[1]** | array of objects | 🌑 | 相關連結列表 |

`[1]`

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `type` | string | 🌕 | 類型 |
| `url` | string | 🌕 | 網址 |
| `title` | string | 🌕 | 標題 |

### Sample input
```json
{
  "status": "active",
  "slug": "a/b/c",
  "image": "path/image.png",
  "st_id": 1,
  "tagline": "選賢與能，選錯了怎麼辦？",
  "title": "罷免議題綜覽",
  "intro": "從歐巴馬這個例子，更加可以理解到，連美國人自己針對台灣問題也經常說不清楚。",
  "description": "從歐巴馬這個例子，更加可以理解到，連美國人自己針對台灣問題也經常說不清楚。",
  "timeline_id": 1,
  "related_links": [
    {
      "type": "type",
      "url": "https://path/to/dest",
      "title": "Lorem ipsum."
    }
  ]
}
```

### Response
> Returns the newly created topic overview

## Update a topic overview
```
PATCH /console/lab/topic_overview/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create a topic overview](#create-a-topic-overview)

## Delete a topic overview
```
DELETE /console/lab/topic_overview/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
