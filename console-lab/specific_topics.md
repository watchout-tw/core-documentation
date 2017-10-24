# Specific Topic

- [List specific topics](#list-specific-topics)
- [Get a single specific topic](#get-a-single-specific-topic)
- [Create a specific topic](#create-a-specific-topic)
- [Update a specific topic](#update-a-specific-topic)
- [Delete a specific topic](#delete-a-specific-topic)

## List specific topics
```
GET /console/lab/specific_topics
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `title` | string | 用標題過濾小議題清單 | partial | `人` `正義` |
| `gt` | integer: general topic ID | 用關聯大議題 ID 過濾小議題清單 | exact | `1` `42` |

### Response
```
{
  rows: [
    {
      id,
      title,
      index,
      image,
      general_topics: [
        {
          id,
          title,
          index,
          image
        }
        ...
      ],
      act_dirs: [
        {
          id,
          name,
          index
        }
        ...
      ],
      st_questions: [
        {
          id,
          question,
          index
        }
        ...
      ]
    }
    ...
  ],
  totalRowCount
}
```

## Get a single specific topic
```
GET /console/lab/specific_topics/:id
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
  general_topics: [
    {
      id,
      title,
      index,
      image
    }
    ...
  ],
  act_dirs: [
    {
      id,
      name,
      index
    }
    ...
  ],
  st_questions: [
    {
      id,
      question,
      index
    }
    ...
  ]
}
```

## Create a specific topic
```
POST /console/lab/specific_topics
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
| `general_topics` | array of integers: general topic IDs | 🌕 | 關聯大議題 ID 列表 |
| `act_dirs` **[1]** | array of objects | 🌑 | 這個小議題的修法方向列表 |
| `st_questions` **[2]** | array of objects | 🌑 | 這個小議題的爭點列表 |

`[1]`

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `name` | string | 🌕 | 標題 |
| `index` | integer | 🌕 | 排序 |

`[2]`

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `question` | string | 🌕 | 標題 |
| `index` | integer | 🌕 | 排序 |


### Sample input
```json
{
  "title": "罷免",
  "index": 1,
  "image": "path/to/image.png",
  "description": "Lorem ipsum.",
  "general_topics": [
    1, 2, 3
  ],
  "act_dirs": [
    {
      "name": "降低罷免門檻",
      "index": 1
    }
  ],
  "st_questions": [
    {
      "question": "你支持下修罷免門檻嗎",
      "index": 1
    }
  ]
}
```

### Response
> Returns the newly created specific topic

## Update a specific topic
```
PATCH /console/lab/specific_topics/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create a specific topic](#create-a-specific-topic)

## Delete a specific topic
```
DELETE /console/lab/specific_topics/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
