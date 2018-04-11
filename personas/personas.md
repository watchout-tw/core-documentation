# Public info of a persona

## Public info of a persona
```
GET /personas/:id
```
### Auth
NO

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
  ]
  latest_status_update: { // [1]
    content
    data: {}
  }
}
```
