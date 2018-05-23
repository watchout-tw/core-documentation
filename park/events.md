# Event

- [List events](#list-events)
- [Get a single event](#get-a-single-event)

## List events
```
GET /park/events
```

### Auth
NO

### Paging
YES

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
  paging: {
    pages
    pageSize
    previous
    next
    page
  }
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
