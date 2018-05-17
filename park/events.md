# Event

- [List events](#list-events)
- [Get a single event](#get-a-single-event)
- [Create an event](#create-an-event)
- [Update an event](#update-an-event)

## List events
```
GET /park/events
```

### Auth
NO

### Paging
NO

### Response
```
{
  rows: [
    {
      id
      status
      slug
      type
      category
      image
      tagline
      title
      before_title
      after_title
      description
      start_date
      end_date
      is_all_day
      location: {}
      repeat_rules: {}
      next_actions: {}
      documentation: {}
      related_content: {}
      data: {}
      collaborators: [
        {
          entity_type,
          entity: {
            id
            ... // entity data
          }
          type
          index
          status
          data: {}
        }
        ...
      ]
    }
    ...
  ]
  totalRowCount
}
```

## Get a single event
```
GET /park/events/:id
```

### Auth
NO

### Paging
NO

### Response
```
{
  id
  status
  slug
  type
  category
  image
  tagline
  title
  before_title
  after_title
  description
  start_date
  end_date
  is_all_day
  location: {}
  repeat_rules: {}
  next_actions: {}
  documentation: {}
  related_content: {}
  data: {}
  collaborators: [
    {
      entity_type,
      entity: {
        id
        ... // entity data
      }
      type
      index
      status
      data: {}
    }
    ...
  ]
}
```

## Create an event
```
POST /park/events
```

### Auth
- `editor`

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `status` | string | 🌑 | 此事件的狀態 |
| `slug` | string | 🌕 | 此事件的短網址 |
| `type` | string | 🌕 | 此事件的類型，如 ask_match |
| `category` | array of strings | 🌕 | 此事件的種類，如 livesteam |
| `image` | string | 🌑 | 此事件的封面圖片連結 |
| `tagline` | string | 🌑 | 此事件的標語 |
| `title` | string | 🌕 | 此事件的標題 |
| `before_title` | string | 🌑 | 此事件的 before_title |
| `after_title` | string | 🌑 | 此事件的 after_title |
| `description` | string | 🌑 | 此事件的詳細敘述 |
| `start_date` | timestamp | 🌑 | 此事件的開始日期 |
| `end_date` | timestamp | 🌑 | 此事件的結束日期 |
| `is_all_day` | boolean | 🌑 | 此事件是否為整天 |
| `location` | JSON | 🌑 |  |
| `repeat_rules` | JSON | 🌑 |  |
| `next_actions` | JSON | 🌑 |  |
| `documentation` | JSON | 🌑 |  |
| `related_content` | JSON | 🌑 |  |
| `data` | JSON | 🌑 |  |
| `collaborators` | array of integers: persona IDs | 🌑 | 此事件的共同舉辦 persona |

## Update an event
```
PATCH /park/events/:id
```

### Auth
- `editor`

### Paging
NO

> 參考 [Create a event](#create-a-event)
