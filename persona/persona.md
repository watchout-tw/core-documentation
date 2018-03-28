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
