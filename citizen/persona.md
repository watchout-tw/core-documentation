# Persona

## List personas

### Auth
- “citizen” AND “self”

### Paging
NO

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `citizen` | int | 用citizenID過濾黨團清單 | exact | `1` `42` |

### Response
```
[
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
    latest_status_update
  }
  ...
]
