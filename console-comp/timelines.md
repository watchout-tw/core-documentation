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

### Auth
- “editor”

### Paging
NO

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `title` | string | 用標題過濾大事紀 | partial | `建` `建國` |

### Response
```
{
  rows: [
    {
      id
      status
      type
      title
    }
    ...
  ]
  totalRowCount
}
```

# Timeline

## Get a single timeline
```
GET /console/comp/timelines/:id
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
  image
  title
  description
  events: [
    {
      id
      status
      slug
      date
      type
      image
      tagline
      title
      content
      link
      data: *JSON*
    }
    ...
  ]
}
```

### Types of timeline event & data format
> timeline中每個event根據type的不同，data的格式也有所不同

#### `term_start`
```
{
  term_index
}
```

#### `session_start`
```
{
  term_index
  session_index
  temp_session_index
}
```

#### `reps_assume_office`
```
{
  reps: [
    *repObject* // GET /c0ngress/date-to-rep-info?date=[date of timeline event]
    ...
  ]
}
```

#### `rs_statements`
```
{
  rs_statements: [
    *rsStatementObject* // GET /c0ngress/rs_statements/:id
    ...
  ]
}
```

#### `rs_bills`
```
{
  rs_bills: [
    *rsBillObject* // GET /c0ngress/rs_bills/:id
    ...
  ]
}
```

#### `bill_legislative_step`
```
{
  rs_bill: *rsBillObject* // GET /c0ngress/rs_bills/:id
  legislative_step_id
}
```

#### `rs_votes`
```
{
  rs_votes: [
    *rsVoteObject* // GET /c0ngress/rs_votes/:id
    ...
  ]
}
```

#### `data_reports`
```
{
  date_reports: [
    *dataReportObject*
    ...
  ]
}
```

> 這裡使用`GET /lab/data_reports`的精簡格式（`GET /lab/data_reports/:id`的資料太多了，不需要）

#### `insights`
```
{
  insights: [
    *insightObject* // GET /lab/insights/:id
  ]
}
```
#### `social_event`
> 按照db裡面的JSON string轉成JSON object

#### `general_update`
> 按照db裡面的JSON string轉成JSON object


## Create a timeline
```
POST /console/comp/timelines
```

### Auth
- “editor”

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `status` | string | 🌕 | 狀態 |
| `slug` | string | 🌕 | 短網址 |
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

### Auth
- “editor”

### Paging
NO

> 參考 [Create a timeline](#create-a-timeline)

## Delete a timeline
```
DELETE /console/lab/timelines/:id
```

### Auth
- “editor”

### Paging
NO

### Response
```javascript
204 No Content
```
