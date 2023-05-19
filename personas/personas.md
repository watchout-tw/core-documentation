# Get a list of personas by role

```
GET /personas/role/_roleID
```

### Auth
NO

### Paging
NO

### Available query parameters
roleID:

2: editor

21: collaborator

22: watchout-editor

23: console-editor

### Response
```
{
  rows: [
    {
      type
      status
      title
      name
      avatar: {}
      start_date
      end_date
      data: {}
    }
    ...
  ]
}
```
