# General Topic

- [List general topics](#list-general-topics)
- [Get a single general topic](#get-a-single-general-topic)
- [Create a general topic](#create-a-general-topic)
- [Update a general topic](#update-a-general-topic)
- [Delete a general topic](#delete-a-general-topic)

## List general topics
```
GET /console/lab/general_topics
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `title` | string | 用標題過濾大議題清單 | partial | `人` `正義` |

### Response
```
{
  rows: [
    {
      id,
      title,
      index,
      image,
      specific_topics: [
        {
          id,
          title,
          index,
          image
        }
        ...
      ]
    }
    ...
  ],
  totalRowCount
}
```

## Get a single general topic
```
GET /console/lab/general_topics/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```
{
  id,
  title,
  index,
  image,
  description,
  specific_topics: [
    {
      id,
      title,
      index,
      image
    }
    ...
  ]
}
```

## Create a general topic
```
POST /console/lab/general_topics
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `title` | string | 🌕 | 標題 |
| `index` | integer | 🌕 | 排序 |
| `image` | string | 🌕 | 圖像 |
| `description` | string | 🌕 | 敘述 |
| `specific_topics` | array of integers: specific topic IDs | 🌕 | 關聯小議題 ID 列表 |


### Sample input
```json
{
  "title": "人民參政",
  "index": 1,
  "image": "path/to/image.png",
  "description": "Lorem ipsum.",
  "specific_topics": [
    1, 2, 3
  ]
}
```

### Response
> Returns the newly created general topic

## Update a general topic
```
PATCH /console/lab/general_topics/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create a general topic](#create-a-general-topic)

## Delete a general topic
```
DELETE /console/lab/general_topics/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
