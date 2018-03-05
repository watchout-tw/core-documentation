# Match of ASK

## List matches
```
GET /ask/matches
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
      index
      status
      type
      game: {}
      event: { // GET /park/events/:id
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
        documentation: [
          {
            type
            [platform]
            id
            title
            description
          }
          ...
        ]
        related_content: [
          {}
          ...
        ]
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
      data: {}
    }
    ...
  ]
  totalRowCount
}
```

## Get a single match
