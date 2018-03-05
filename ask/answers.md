# Answer of ASK

## List answers
```
GET /ask/answers
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
      status
      slug
      index
      image
      content
      question
      persona
      references: []
      data: {}
    }
    ...
  ]
  totalRowCount
}
```

## Get a single answer
