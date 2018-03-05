# Timeline

## Get a single timeline
```
GET /comp/timelines/:id
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
