# Timeline

## Get a single timeline
```
GET /comp/timelines/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

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

### Types of timeline event
> timeline中每個event根據type的不同，data的格式也有所不同

#### `term_start`
```
{
  term_index: 8
}
```

#### `session_start`
#### `reps_assume_office`
#### `rs_statements`
#### `rs_bills`
#### `bill_legislative_step`
#### `rs_votes`
#### `data_reports`
#### `insights`
#### `social_event`
#### `general_update`
