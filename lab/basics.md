# List specific topics
```
GET /lab/specific_topics
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Response
```
{
  rows: [
    {
      id
      title
      index
      image
      description
    }
    ...
  ]
  totalRowCount
}
```

# List ST questions
```
GET /lab/st_questions
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Response
```
{
  rows: [
    {
      id
      st_id
      question
      index
    }
    ...
  ]
  totalRowCount
}
```
