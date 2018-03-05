# ?

- [List ?s](#list-?s)
- [Get a single ?](#get-a-single-?)
- [Create a ?](#create-a-?)
- [Update a ?](#update-a-?)
- [Delete a ?](#delete-a-?)

## List ?s
```
GET /console/lab/?s
```

### Auth
- “editor”

### Paging
YES

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |

### Response
```
{
  rows: [
    {
    }
    ...
  ]
  totalRowCount
  paging: {
    page
    pages
    pageSize
    previous
    next
  }
}
```

## Get a single ?
```
GET /console/lab/?s/:id
```

### Auth
- “editor”

### Paging
NO

### Response
```
{
}
```

## Create a ?
```
POST /console/lab/?s
```

### Auth
- “editor”

### Paging
NO

### Input

| Key | Type | Description |
| --- | --- | --- |

### Sample input
```json
{
}
```

### Response
> Returns the newly created ?

## Update a ?
```
PATCH /console/lab/?s/:id
```

### Auth
- “editor”

### Paging
NO

### Input

| Key | Type | Description |
| --- | --- | --- |

### Sample input
```json
{
}
```

### Response
> Returns the updated ?

## Delete a ?
```
DELETE /console/lab/?s/:id
```

### Auth
- “editor”

### Paging
NO

### Response
```javascript
204 No Content
```
