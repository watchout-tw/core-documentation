# Persona (author)

- [Get active author](#get-active-author)

## Get active author
```
GET /personas/author/_id
```

### Auth
NO

### Paging
NO

### Response
```
{
  id
  citizen_id
  email
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
  ]
  latest_status_update: { // [1]
    content
    data: {}
  }
}
```

### Sample
```json
{
  "id": 6,
  "citizen_id": 6,
  "type": "default",
  "status": "active",
  "title": null,
  "name": "林家偉",
  "avatar": {
      "id": "default",
      "type": "system"
  },
  "start_date": null,
  "end_date": null,
  "data": null,
  "concerned_topics": [],
  "latest_status_update": {
      "data": null,
      "content": "願我成為一個柔軟且堅定的人"
  },
  "email": "wesley.lin@watchout.tw"
}
```
