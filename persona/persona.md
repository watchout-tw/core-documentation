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
  latest_status_update
}
```
