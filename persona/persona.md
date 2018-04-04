# Persona

## Get active persona
```
GET /persona
```

### Auth
- “citizen” AND “self”

### Paging
NO

### Response
```
{
  type
  status
  title
  name
  avatar
  start_date
  end_date
  data: {}
  concerned_topics: [
    {
      topic_type
      topic_id
    }
    ...
  ],
  latest_status_update: { // [1]
    content
    data: {}
  }
}
```

`[1]`
> persona_id與active persona相同，且create_date最新的Persona_Status_Update

## Update active persona
```
PATCH /persona
```

### Auth
- “citizen” AND “self”

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `title` | string | 🌑 | 抬頭 |
| `name` | string | 🌑 | 顯示名稱 |
| `avatar` | JSON | 🌑 | 頭像 |
| `concerned_topics` | JSON: array of topic IDs | 🌑 | 我關心的議題；至多三項 |
| `status_update` | string | 🌑 | 一句話 |

### Sample input
```json
{
  "title": "排球國手",
  "name": "黃培閎",
  "concerned_topics": [
    1, 2, 4
  ],
  "status_update": "贏回排球！"
}
```

### Response
> ?
