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

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌕 |

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
  ],
  totalRowCount
}
```

## Get a single ?
```
GET /console/lab/?s/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```
{
}
```

## Create a ?
```
POST /console/lab/?s
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

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

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

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

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
